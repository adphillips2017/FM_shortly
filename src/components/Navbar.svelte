<script lang="ts">
  let displayNav: boolean = false;

  const toggleNav = (): void => {
    displayNav = !displayNav;
  };
</script>

<div class="nav">
  <img class="logo" src="build/images/logo.svg" alt="logo.svg" />
  <div class="link txt-gray desktop">Features</div>
  <div class="link txt-gray desktop">Pricing</div>
  <div class="link txt-gray desktop">Resources</div>
  <div class="spacer" />
  <div class="link txt-gray desktop">Login</div>
  <div class="btn btn-rounded desktop">Sign Up</div>

  <img
    on:click={toggleNav}
    class="menu-button"
    src="build/images/menu-icon.svg"
    alt="menu.svg"
  />

  <div class="mobile-menu br-tight {displayNav ? '' : 'd-none'}">
    <div class="menu-item">Features</div>
    <div class="menu-item">Pricing</div>
    <div class="menu-item">Resources</div>
    <hr />
    <div class="menu-item">Login</div>
    <div class="btn btn-rounded">Sign Up</div>
  </div>
</div>

<style>
  .nav {
    display: flex;
    align-items: center;
    font-size: 0.85rem;
    position: relative;
  }

  .logo {
    margin-right: 1rem;
  }

  .link {
    margin-left: 1.5rem;
  }

  .link:hover, .menu-item:hover {
    color: var(--cyan);
    cursor: pointer;
  }

  .btn {
    margin-left: 2rem;
  }

  .spacer {
    flex-grow: 1;
  }

  .menu-button {
    display: none;
  }

  .d-none {
    display: none;
  }

  .mobile-menu {
    margin: auto;
    background-color: var(--dark_violet);
    padding: 2rem;
    position: absolute;
    top: 5rem;
    width: 70vw;
  }

  .menu-item {
    text-align: center;
    margin-bottom: 2rem;
    color: white;
  }

  hr {
      margin-bottom: 2rem;
      border: 1px solid var(--gray_violet);
  }

  @media (max-width: 825px) {
    .desktop {
      display: none;
    }

    .menu-button {
      display: block;
      cursor: pointer;
    }

    .btn {
        margin-left: 0;
    }
  }
</style>
