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
        <!--<p>Simplifying Legislature</p>-->
        <p>
          We're here to boost your involvement in shaping our community, by making sure your voice is heard. Together, let's build a more informed and inclusive democracy where your input matters. 
          </p>
      
        </section>
</main>

<style>
  .hero {
    /*background: #fffff4;*/
    /*background: white;*/
    background-image: url("s_NJ Capitol building(1).jpg");
    background-size: cover;
  }

  .hero-container {
    display: grid;
    grid-template-columns: 1fr;
    height: 95vh;
    padding: 3rem calc((100vw - 1300px) / 2);
  }

  .column-left {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: #000;
    padding: 0rem 15rem;
    text-align: center;
  }

  .column-left h1 {
    font-family: 'Rabbid Highway Sign IV', sans-serif;
    /*font-style: italic;*/
    margin-bottom: 1rem;
    font-size: 4rem;
    color: aliceblue;
  }

  .column-left p {
    font-family: 'Varela', sans-serif;
    margin-bottom: 2rem;
    font-size: 1.5rem;
    line-height: 1.5;
    color: aliceblue;
  }
/*
  .column-right {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0rem 2rem;
  }
*/
  @media screen and (max-width: 768px) {
    .hero-container {
      grid-template-columns: 1fr;
    }
  }
</style>
