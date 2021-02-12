<script lang="ts">
	import Navbar from './components/Navbar.svelte';
	import PhotoHeader from './components/PhotoHeader.svelte';
	import LinkShortener from './components/LinkShortener.svelte';
</script>

<main>
<div class="main-container">
	<Navbar />
	<div class="spacer-7"></div>

	<PhotoHeader />
	<div class="spacer-4"></div>

	<LinkShortener />
	<div class="spacer-4"></div>
</div>
</main>

<style>
	.main-container {
		padding-top: 2rem;
		padding-left: 8rem;
		padding-right: 8rem;
	}

	.spacer-7 {
		height: 7rem;
	}
	.spacer-4 {
		height: 4rem;
	}
</style>