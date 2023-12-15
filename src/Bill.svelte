<script lang="ts">
  let weLoveCookies: HTMLParagraphElement,
    title: HTMLInputElement,
    reasoning: HTMLInputElement,
    date: HTMLInputElement;

  function myFunction() {
    if (reasoning != null) {
      weLoveCookies.innerHTML =
        "Write me a proposed bill for the New Jersey legislature titled " +
        title.value +
        " along with 3 clauses: one clause that explains why it is important and " +
        reasoning.value +
        ", one clause with the actions it will take to achieve it, and one enactment clause under the previous clause that clearly explains the actions that will be made and states the date that it will be passed: " +
        date;
    } else {
      weLoveCookies.innerHTML =
        "Write me a proposed bill for the New Jersey legislature titled " +
        title.value +
        " along with 3 clauses: one clause that explains why it is important, one clause with the actions it will take to achieve it, and one enactment clause under the previous clause that clearly explains the actions that will be made and states the date that it will be passed";
    }
  }
</script>

<svelte:head>
  <title>OurState - Bill Archive</title>
</svelte:head>

<div class="format">
  <br />
  <br />
  <span>Please enter your bill's name:</span>
  <br />
  <input type="text" bind:this={title} placeholder="Title" />
  <br />
  <br />
  <span>Why do you want to pass this bill:</span>
  <br />
  <input type="text" bind:this={reasoning} placeholder="Reasoning" />
  <br />
  <br />
  <span
    > (Optional) What is the date you want to pass this bill by? In [Month],[Day],[Year]
    format:</span
  >
  <br />
  <input type="text" bind:this={date} placeholder="Date" />
  <br />
  <br />
  <button on:click={myFunction}>Submit</button>
</div>

<p bind:this={weLoveCookies} />

  <!-- powr BEGIN --><div class="powr-form-builder" id="sharethis-form-builder-651a0aefd43c16001201d81d"></div><!-- powr END -->

<style>
  .format {
    margin-left: 5rem;
    white-space: flex;
  }

  span {
    font-size: 2rem;
  }

  input {
    border: 2px var(--fg) solid;
    width: 20rem;
    height: 2rem;
    font-size: 1.5rem;
    background-color: var(--bg);
  }

  button {
    padding: .625rem;
    font-size: 1.25rem;
    border: none;
    background-color: var(--blue);
    color: var(--bg);
    cursor: pointer;
    border-radius: 1rem;
  }

  button:hover {
    background-color: var(--dim-bg);
    color: var(--fg);
    border-radius: .5rem;
  }
</style>
