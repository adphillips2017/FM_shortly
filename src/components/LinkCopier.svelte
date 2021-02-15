<script lang="ts">
  import type { ShortenedLink } from "../models/ShortenedLink";

  export let link: ShortenedLink;
  let copied: boolean = false;

  const handleClick = (): void => {
    var textArea = document.createElement("textarea");

    // Place in the top-left corner of screen regardless of scroll position.
    textArea.style.position = "fixed";
    textArea.style.top = "0";
    textArea.style.left = "0";

    // Ensure it has a small width and height. Setting to 1px / 1em
    // doesn't work as this gives a negative w/h on some browsers.
    textArea.style.width = "2em";
    textArea.style.height = "2em";

    // We don't need padding, reducing the size if it does flash render.
    textArea.style.padding = "0";

    // Clean up any borders.
    textArea.style.border = "none";
    textArea.style.outline = "none";
    textArea.style.boxShadow = "none";

    // Avoid flash of the white box if rendered for any reason.
    textArea.style.background = "transparent";

    textArea.value = link.shortLink;

    document.body.appendChild(textArea);
    textArea.focus();
    textArea.select();

    try {
      var successful = document.execCommand("copy");
      setCopied(!!successful);
    } catch (err) {
      console.error("Oops, unable to copy");
    }

    document.body.removeChild(textArea);
  };

  const setCopied = (state: boolean): void => {
    copied = state;
    if (copied) {
      setTimeout(() => {
        copied = false;
      }, 2000);
    }
  };
</script>

<main>
  <div class="container br-tight">
    <span class="long-link">{link.longLink}</span>
    <div class="short-link-container">
      <span class="short-link" id="shortLink">{link.shortLink}</span>
      <div on:click={handleClick} class="btn br-tighter {copied ? 'copied' : ''}" >
        {#if copied}
          Copied!
        {:else}
          Copy
        {/if}
      </div>
    </div>
  </div>
</main>

<style>
  .container {
    display: flex;
    justify-content: space-between;
    padding: 1.5rem;
    background-color: white;
    align-items: center;
  }

  .long-link {
    max-width: 50%;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  .short-link-container {
    display: flex;
    align-items: center;
  }

  .short-link {
    color: var(--cyan);
    margin-right: 1rem;
  }

  .btn {
    background-color: var(--cyan);
    color: white;
    width: 5rem;
    padding: 1rem;
    padding-top: 0.5rem;
    padding-bottom: 0.5rem;
    text-align: center;
    font-size: 0.8rem;
    border: 1px solid var(--cyan);
    transition: background-color 1s;
  }

  .copied {
    background-color: var(--dark_violet);
    border-color: var(--dark_violet);
  }

  .copied:hover {
    background-color: var(--dark_violet) !important;
    border-color: var(--dark_violet) !important;
    color: white !important;
    cursor: none;
  }
</style>
