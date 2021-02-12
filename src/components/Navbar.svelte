<div class="nav">
    <img class="logo" src="build/images/logo.svg" alt="logo.svg">
    <div class="link txt-gray">Features</div>
    <div class="link txt-gray">Pricing</div>
    <div class="link txt-gray">Resources</div>
    <div class="spacer"></div>
    <div class="link txt-gray">Login</div>
    <div class="btn btn-rounded">Sign Up</div>
</div>

<style>
    .nav {
        display: flex;
        align-items: center;
        font-size: .85rem;
    }

    .logo {
        margin-right: 1rem;
    }

    .link {
        margin-left: 1.5rem;
        cursor: pointer;
    }

    .link:hover {
        color: var(--cyan);
    }

    .btn {
        margin-left: 2rem;
    }

    .spacer {
        flex-grow: 1;
    }
</style>