<script lang="ts">
  import { createEventDispatcher } from "svelte";

  const dispatcher = createEventDispatcher();
  function legislature() {
    dispatcher("legislature");
  }
</script>

<svelte:head>
  <title>OurState - Home</title>
</svelte:head>

<main>
  <section class="hero">
    <div class="hero-container">
      <div class="column-left">
        <h1>OurState</h1>
        <p>Simplifying Legislature</p>
        <p>
          OurState aims to increase civic engagement, promote transparency, and bridge the gap between voters and lawmakers. Ultimately, the goal is to create a more informed, participatory democracy where every citizen has a voice in the decisions that affect their lives.
        </p>
        <!--<button on:click={legislature}>Find Legislature</button>-->
      </div>
      <div class="column-right">
        <!--Image-->
      </div>
    </div>
  </section>
</main>

<style>
  .hero {
    background: #fdcc04;
  }

  .hero-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    height: 95vh;
    padding: 3rem calc((100vw - 1300px) / 2);
  }

  .column-left {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    color: #000;
    padding: 0rem 2rem;
  }

  .column-left h1 {
    margin-bottom: 1rem;
    font-size: 3rem;
  }

  .column-left p {
    margin-bottom: 2rem;
    font-size: 1.5rem;
    line-height: 1.5;
  }

  .column-right {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0rem 2rem;
  }

  @media screen and (max-width: 768px) {
    .hero-container {
      grid-template-columns: 1fr;
    }
  }
</style>
