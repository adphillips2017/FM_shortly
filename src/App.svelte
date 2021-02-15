<script lang="ts">
  import Navbar from "./components/Navbar.svelte";
  import PhotoHeader from "./components/PhotoHeader.svelte";
  import LinkShortener from "./components/LinkShortener.svelte";
  import LinkCopier from "./components/LinkCopier.svelte";
  import type { ShortenedLink } from "./models/ShortenedLink";

  let links: ShortenedLink[] = [];

  const handleShortLink = (event) => {
    links = [...links, event.detail];
  };
</script>

<main>
  <div class="bg-white">
    <div class="main-container container">
      <Navbar />
      <div class="spacer-7" />

      <PhotoHeader />
      <div class="spacer-4" />
    </div>
  </div>

  <div class="container secondary-container">
    <LinkShortener on:shortLinkCreated={handleShortLink} />
    <div class="spacer-1" />

    {#each links as link}
      <LinkCopier {link} />
      <div class="spacer-1" />
    {/each}

    <div class="spacer-4" />
  </div>
</main>

<style>
  .container {
    padding-top: 2rem;
    padding-left: 8rem;
    padding-right: 8rem;
  }

  .main-container {
    padding-bottom: 6rem;
  }

  .secondary-container {
    margin-top: -6.5rem;
  }

  .spacer-7 {
    height: 7rem;
  }
  .spacer-4 {
    height: 4rem;
  }
  .spacer-1 {
    height: 1.5rem;
  }
</style>
