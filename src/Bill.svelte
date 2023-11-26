<script lang="ts">
  function myFunction() {
    let title = document.getElementById("title") as HTMLInputElement;
    let reasoning = document.getElementById("reasoning") as HTMLInputElement;
    let date = document.getElementById("date") as HTMLInputElement;

    if (reasoning != null) {
      document.getElementById("welovecookies").innerHTML =
        "Write me a proposed bill for the New Jersey legislature titled " +
        title +
        " along with 3 clauses: one clause that explains why it is important and " +
        reasoning +
        ", one clause with the actions it will take to achieve it, and one enactment clause under the previous clause that clearly explains the actions that will be made and states the date that it will be passed: " +
        date;
    } else {
      document.getElementById("welovecookies").innerHTML =
        "Write me a proposed bill for the New Jersey legislature titled " +
        title +
        " along with 3 clauses: one clause that explains why it is important, one clause with the actions it will take to achieve it, and one enactment clause under the previous clause that clearly explains the actions that will be made and states the date that it will be passed";
    }
  }
</script>

<svelte:head>
  <title>OurState - Bill Archive</title>
  <!-- Google tag (gtag.js) -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-9EG14MZYZM"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'G-9EG14MZYZM');
  </script>
</svelte:head>

<main>
  <body class="hero">
    <div class="format">
      <br />
      <br />
      <span>Please enter your bill's name:</span>
      <br />
      <input type="text" id="title" placeholder="Title" />
      <br />
      <br />
      <span>Why do you want to pass this bill:</span>
      <br />
      <input type="text" id="reasoning" placeholder="Reasoning" />
      <br />
      <br />
      <span
        >What is the date you want to pass this bill by? In [Month],[Day],[Year]
        format (optional):</span>
      <br />
      <input type="text" id="Date" placeholder="Date" />
      <br />
      <br />
      <button on:click={myFunction}>Submit</button>
    </div>

    <p id="welovecookies" />
  </body>
</main>

<style>
  .hero {
    background: #fffff4;
    height: 40.7rem;
  }

  .format {
    margin-left: 5rem;
    white-space: nowrap;
  }

  span {
    font-family: "Titillium Web", sans-serif;
    font-size: 2rem;
  }

  input {
    border-color: black;
    border-style: solid;
    border-width: 2px;
    width: 20rem;
    height: 2rem;
    font-size: 1rem;
    background-color: #fffff4;
  }

  button {
    padding-left: 1rem;
    padding-right: 1rem;
    font-size: 2rem;
    border: none;
    color: #fffff4;
    background: #000;
    cursor: pointer;
    border-radius: 50px;
    height: 5rem;
    width: 10rem;
  }

  button:hover {
    background: #fff;
    color: #000;
  }
</style>
