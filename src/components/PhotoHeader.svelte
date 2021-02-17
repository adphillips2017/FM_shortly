<div class="photo-header">
  <div class="text">
    <div class="header txt-heavy">More than just shorter links</div>
    <div class="subtitle txt-gray">
      Build your brand's recognition and get detailed insights on how your links
      are performing.
    </div>
    <div class="btn btn-rounded-lg">Get Started</div>
  </div>

  <img
    class="illustration"
    src="build/images/illustration-working.svg"
    alt="working.svg"
  />
</div>

<style>
  .photo-header {
    display: flex;
  }

  .text {
    width: 30rem;
    flex-shrink: 0;
  }

  .header {
    font-size: 4rem;
    line-height: 4.5rem;
    margin-bottom: 1rem;
  }

  .subtitle {
    margin-bottom: 2rem;
  }

  .illustration {
    margin-top: -4rem;
    margin-left: 4rem;
  }

  @media (max-width: 825px) {
    .photo-header {
      flex-direction: column-reverse;
    }

    .illustration {
      margin-left: 0;
      height: 26rem;
      width: fit-content;
    }

    .text {
        text-align: center;
        width: auto;
    }

    .header {
        margin-bottom: 1rem;
        margin-top: 2rem;
        font-size: 3rem;
        font-weight: 800;
        line-height: 3.5rem;
    }

    .btn {
        margin: auto;
    }
  }
</style>
