<script lang="ts">
  import Navbar from "./components/Navbar.svelte";
  import PhotoHeader from "./components/PhotoHeader.svelte";
  import LinkShortener from "./components/LinkShortener.svelte";
  import LinkCopier from "./components/LinkCopier.svelte";
  import Statistics from './components/Statistics.svelte';
  import CallToAction from './components/CallToAction.svelte';
  import Footer from './components/Footer.svelte';

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
    <Statistics />
    <div class="spacer-4"></div>
  </div>

  <CallToAction />
  <Footer />
</main>

<style>
  .container {
    padding-top: 2rem;
    width: 95%;
    margin: auto;
    max-width: 70rem;
  }

  .main-container {
    padding-bottom: 6rem;
  }

  .secondary-container {
    margin-top: -6.5rem;
  }

  @media (max-width: 825px) {
      .container {
          width: 85%;
          margin: auto;
          padding-left: 0;
          padding-right: 0;
      }

      .main-container {
          padding-bottom: 0;
      }
  }
</style>
