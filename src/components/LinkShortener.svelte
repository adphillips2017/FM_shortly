<div class="container">
    <div class="bg-container br-tight">
        <input placeholder="Shorten a link here..." type="text" class="br-tight" id="userInput" aria-label="Link to shorten">
        <div class="btn btn-rounded-lg br-tight">Shorten it!</div>
    </div>
</div>

<style>
    .bg-container {
        background-image: url('images/bg-shorten-desktop.svg');
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
</style>