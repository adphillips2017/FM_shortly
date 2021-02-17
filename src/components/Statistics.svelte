<main>
  <div class="container">
    <div class="header">
      <div class="title">Advanced Statistics</div>
      <div class="txt-gray">
        Track how your links are performing across the web with our advanced
        statistics dashboard.
      </div>
    </div>

    <div class="blue-line">
      <div class="blue-line-h" />
      <div class="stat-card br-tighter left">
        <div class="stat-logo">
          <img
            class="logo"
            src="build/images/icon-brand-recognition.svg"
            alt="graph.svg"
          />
        </div>

        <div class="stat-title">Brand Recognition</div>
        <div class="txt-gray content">
          Boost your brand recognition with each click. Generic links don't mean
          a thing. Branded links help instil confidence in your txt-gray.
        </div>
      </div>

      <div class="stat-card br-tighter center">
        <div class="stat-logo">
          <img
            class="logo"
            src="build/images/icon-detailed-records.svg"
            alt="speed.svg"
          />
        </div>

        <div class="stat-title">Detailed Records</div>
        <div class="txt-gray content">
          Gain insights into who is clicking your links. Knowing when and where
          people engage with your content helps inform better decisions.
        </div>
      </div>

      <div class="stat-card br-tighter right">
        <div class="stat-logo">
          <img
            class="logo"
            src="build/images/icon-fully-customizable.svg"
            alt="custom.svg"
          />
        </div>

        <div class="stat-title">Fully Customizable</div>
        <div class="txt-gray content">
          Improve brand awareness and content discoverability through
          customizable links, supercharging audience engagement.
        </div>
      </div>
    </div>
  </div>
</main>

<style>
  .header {
    width: 32rem;
    margin: auto;
    text-align: center;
  }

  .title {
    font-weight: 800;
    font-size: 2.5rem;
    white-space: nowrap;
    margin-bottom: 0.5rem;
  }

  .blue-line {
    border-top: 0.5rem solid var(--cyan);
    display: flex;
    z-index: 0;
    justify-content: space-between;
    margin-top: 16rem;
  }

  .blue-line-h {
    display: none;
  }

  .stat-card {
    background-color: white;
    padding: 2rem;
    padding-top: 4rem;
    width: 25%;
    height: fit-content;
    position: relative;
  }

  .stat-title {
    margin-bottom: 1rem;
    font-weight: 800;
  }

  .content {
    font-size: 0.75rem;
  }

  .left {
    margin-top: -10rem;
  }

  .center {
    margin-top: -8rem;
  }

  .right {
    margin-top: -6rem;
  }

  .stat-logo {
    height: 4rem;
    width: 4rem;
    background-color: var(--dark_violet);
    border-radius: 50%;
    text-align: center;
    align-self: center;
    position: absolute;
    top: -2rem;
  }

  .logo {
    margin-top: 0.8rem;
  }

  @media (max-width: 825px) {
    .header {
      width: auto;
    }

    .title {
      font-size: 8vw;
    }

    .blue-line {
      flex-direction: column;
      border: none;
      margin-top: 0rem;
      position: relative;
    }

    .stat-card {
      width: auto;
      margin-top: 6rem;
      text-align: center;
    }

    .stat-logo {
      top: -2rem;
      left: calc(50% - 2.5rem);
      height: 5rem;
      width: 5rem;
    }

    .logo {
      margin-top: 1.25rem;
    }

    .blue-line-h {
      position: absolute;
      border-left: 0.5rem solid var(--cyan);
      height: 90%;
      left: 50%;
      top: 4rem;
      display: inline-block;
    }
  }
</style>
