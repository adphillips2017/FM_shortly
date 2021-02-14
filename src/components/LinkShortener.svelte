<script lang="ts">
  import axios from "axios";
  const baseUrl: string = "https://api.shrtco.de/v2/shorten?url=";
  let userInput: string = "";
  let shortLink: string = "";
  let errorMessage: string = "";

  const getShortURL = (longURL: string): void => {
    const apiURL: string = baseUrl + longURL;

    axios
      .post(apiURL)
      .then((response) => {
        const data = response.data;
        console.log("data", data);
        if (data.ok) {
          console.log("short url: ", data.result.short_link);
          shortLink = data.result.short_link;
        }
      })
      .catch((error) => {
        console.error("Error", error, '\nresponse: ', error.response);
        if (error.response.data?.error) {
            errorMessage = error.response.data?.error;
        } else {
            errorMessage = error;
        }
      });
  };

  const handleKeydown = (event): void => {
    errorMessage = "";
    if (event.keyCode === 13) {
      onSubmit();
    }
  };

  const onSubmit = (): void => {
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
      bind:value={userInput}
      on:keydown={handleKeydown}
    />
    <div class="btn btn-rounded-lg br-tight" on:click={onSubmit}>
      Shorten it!
    </div>
  </div>
  {#if errorMessage}
    <div class="error-message">{errorMessage}</div>
  {/if}
</div>
{shortLink}

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
</style>
