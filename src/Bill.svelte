<svelte:head>
  <title>OurState - Bill Archive</title>
</svelte:head>

<main>
<!--TODO, make an input system for this and clean up the code-->
<br>
<br>
<span>Please enter your bill's name:</span>
<br>
<input type="text" id="title" placeholder="Title">
<br>
<br>
<span>Why do you want to pass this bill:</span>
<br>
<input type="text" id="reasoning" placeholder="Reasoning">
<br>
<br>
<span>What is the date you want to pass this bill by? In [Month],[Day],[Year] format (optional):</span>
<br>
<input type="text" id="Date" placeholder="Date">
<br>
<br>
<button on:click={myFunction}>Click Here to Submit</button>


<p id="welovecookies"></p>
</main>
<script lang="ts">

function myFunction() {
  let title = (
      document.getElementById("title") as HTMLInputElement
    );
  let reasoning = (
      document.getElementById("reasoning") as HTMLInputElement
    );
  let date = (
      document.getElementById("date") as HTMLInputElement
    );
 
    if (reasoning != null) {
    document.getElementById("welovecookies").innerHTML =
    "Write me a proposed bill for the New Jersey legislature titled " + title + " along with 3 clauses: one clause that explains why it is important and " + reasoning + ", one clause with the actions it will take to achieve it, and one enactment clause under the previous clause that clearly explains the actions that will be made and states the date that it will be passed: " + date;
  } else {
    document.getElementById("welovecookies").innerHTML =
    "Write me a proposed bill for the New Jersey legislature titled " + title + " along with 3 clauses: one clause that explains why it is important, one clause with the actions it will take to achieve it, and one enactment clause under the previous clause that clearly explains the actions that will be made and states the date that it will be passed";
  }
}

</script>

