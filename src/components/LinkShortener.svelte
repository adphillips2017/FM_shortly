<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import axios from "axios";
  import type { ShortenedLink } from "../models/ShortenedLink";
  import LoadingIcon from "./LoadingIcon.svelte";

  const dispatch = createEventDispatcher();
  const baseUrl: string = "https://api.shrtco.de/v2/shorten?url=";
  let userInput: string = "";
  let shortLink: string = "";
  let errorMessage: string = "";
  let loading: boolean = false;

  const getShortURL = (longURL: string): void => {
    if (loading) {
      return;
    }
    loading = true;
    const apiURL: string = baseUrl + longURL;

    axios
      .post(apiURL)
      .then((response) => {
        const data = response.data;
        if (data.ok) {
          shortLink = data.result.short_link;
          shortLinkCreated(longURL);
          loading = false;
        }
      })
      .catch((error) => {
        console.error("Error", error, "\nresponse: ", error.response);
        if (error.response.data?.error) {
          errorMessage = error.response.data?.error;
        } else {
          errorMessage = error;
        }
        loading = false;
      });
  };

  function shortLinkCreated(longLink: string) {
    const link: ShortenedLink = { shortLink, longLink };
    dispatch("shortLinkCreated", link);
  }

  const handleKeydown = (event): void => {
    errorMessage = "";
    if (event.keyCode === 13) {
      onSubmit();
    }
  };

  const onSubmit = (): void => {
    if (loading) {
      return;
    }
    if (userInput === "") {
      errorMessage = "Please enter a URL to shorten.";
      return;
    }

    getShortURL(userInput);
    resetInput();
  };

  const resetInput = (): void => {
    userInput = "";
    errorMessage = "";
  };
</script>

<div class="container">
  <div class="bg-container br-tight">
    <input
      placeholder="Shorten a link here..."
      type="text"
      class="br-tight {errorMessage !== '' ? 'error' : ''}"
      id="userInput"
      aria-label="Link to shorten"
      disabled={!!loading}
      bind:value={userInput}
      on:keydown={handleKeydown}
    />
    <div
      class="btn btn-rounded-lg br-tight {loading ? 'btn-loading' : ''}"
      on:click={onSubmit}
    >
      {#if loading}
        <span class="spinner"><LoadingIcon /></span>
      {:else}
        Shorten it!
      {/if}
    </div>
  </div>
  {#if errorMessage}
    <div class="error-message">{errorMessage}</div>
  {/if}
</div>

<style>
  .container {
    position: relative;
  }

  .bg-container {
    background-image: url("images/bg-shorten-desktop.svg");
    background-color: var(--dark_violet);
    display: flex;
    padding: 3rem;
  }

  #userInput {
    flex-grow: 1;
    margin-right: 1rem;
    padding: 1rem;
    font-size: var(--text_normal);
  }

  .btn {
    width: 6rem;
    position: relative;
  }

  .btn-loading {
    background-color: var(--gray-violet);
    cursor: progress;
  }

  .btn-loading:hover {
    color: white;
  }

  .error-message {
    color: var(--red);
    position: absolute;
    bottom: 1.75rem;
    left: 3.5rem;
    font-style: italic;
    font-size: 0.7rem;
  }

  .error {
    border: 3px solid var(--red);
    color: var(--red);
  }

  .spinner {
    position: absolute;
    top: 0rem;
    left: 4rem;
  }
</style>
