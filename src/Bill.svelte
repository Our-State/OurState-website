<svelte:head>
  <title>OurState - Bill Archive</title>
</svelte:head>

<main>
<!--TODO, make an input system for this and clean up the code-->
<button on:click={myFunction}>Click here!!!!!!!!!!!</button>
<br>
<br>
<span>Please enter your bill's name:</span>
<br>
<input type="text" id="title" placeholder="Title">
<br>
<br>
<span>Please enter your bill's name:</span>
<br>
<input type="text" id="title" placeholder="Title">


<p id="welovecookies"></p>
</main>
<script>
function myFunction() {
  let title = prompt("Please enter your bill's name", "");
  let reasoning = prompt("Why do you want to pass this bill (optional)", "");
  let date = prompt("What is the date you want to pass this bill by? In [Month],[Day],[Year] format (optional)", "January 1st, 2023");

 
  if (reasoning != null) {

    document.getElementById("welovecookies").innerHTML =
    "Write me a proposed bill for the New Jersey legislature titled " + title + " along with 3 clauses: one clause that explains why it is important and " + reasoning + ", one clause with the actions it will take to achieve it, and one enactment clause under the previous clause that clearly explains the actions that will be made and states the date that it will be passed: " + date;


  } else {

    document.getElementById("welovecookies").innerHTML =
    "Write me a proposed bill for the New Jersey legislature titled " + title + " along with 3 clauses: one clause that explains why it is important, one clause with the actions it will take to achieve it, and one enactment clause under the previous clause that clearly explains the actions that will be made and states the date that it will be passed";

  }
}
</script>

