<script lang="ts">
  import { slide } from "svelte/transition";
  import Bill from "./Bill.svelte";
  import Home from "./Home.svelte";
  import Legislature from "./Legislature.svelte";
  import Recent from "./Recent.svelte";
  import { app } from "./firebase";
  import { GoogleAuthProvider, getAuth, signInWithPopup } from "firebase/auth";

  enum Page {
    Home,
    Legislature,
    Recent,
    Bill,
  }

  let page = Page.Home;
  let isSignedIn = false;
  let isSignInButtonDisabled = false;
  let isSignOutButtonDisabled = false;

  const auth = getAuth();
  const provider = new GoogleAuthProvider();

  function signIn() {
    isSignInButtonDisabled = true;
    signInWithPopup(auth, provider)
      .then(() => (isSignedIn = true))
      .then(() => (isSignInButtonDisabled = false))
      .catch(alert);
  }

  function signOut() {
    isSignOutButtonDisabled = true;
    auth
      .signOut()
      .then(() => (isSignedIn = false))
      .then(() => (isSignOutButtonDisabled = false))
      .catch(alert);
  }
</script>


<main>
  <nav>
    <div class="logo">Welcome to OurState!</div>
    <div class="nav-items">
      <button class="navBar" on:click={() => (page = Page.Home)}>Home</button>
      <button class="navBar" on:click={() => (page = Page.Legislature)}
        >Legislature Archive</button
      >
      <button class="navBar" on:click={() => (page = Page.Recent)}
        >Recent Bills</button
      >
      <button class="navBar" on:click={() => (page = Page.Bill)}
        >Draft Legislation</button
      >
      {#if !isSignedIn}
        {#if !isSignInButtonDisabled}
          <button class="signIn" on:click={signIn}>Sign In</button>
        {:else}
          <button class="signIn" disabled>Sign In</button>
        {/if}
      {:else if !isSignOutButtonDisabled}
        <button class="signIn" on:click={signOut}>Sign Out</button>
      {:else}
        <button class="signIn" disabled>Sign Out</button>
      {/if}
    </div>
  </nav>

  <div class="sharethis-inline-share-buttons"></div>


  {#if page == Page.Home}
    <main transition:slide>
      <Home on:legislature={() => (page = Page.Legislature)} />
    </main>
  {:else if page == Page.Legislature}
    <main transition:slide>
      <Legislature />
    </main>
  {:else if page == Page.Recent}
    <main transition:slide>
      <Recent />
    </main>
  {:else if page == Page.Bill}
    <main transition:slide>
      <Bill />
    </main>
  {/if}
</main>

<style>

  button {
    padding-left: 1rem;
    padding-right: 1rem;
    font-size: 18px;
    border: none;
    font-family: 'Varela', sans-serif;
    color: var(--bg);
    background-color: transparent;
    cursor: pointer;
    border-radius: 1rem;
    height: 2rem;
  }

  .signIn {
    margin-left: 2rem;
  }

  button:hover {
    background: transparent;
    color: #E1D9D1;
    border-radius: .5rem;
  }

  nav {
    height: 80px;
    /*background: color-mix(in srgb, var(--blue) 60%, var(--fg));*/
    background-color: #8c7949;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-left: 10%;
    padding-right: 5%;
  }

  .logo {
    color: #fffff4;
    font-family: "Cabin", sans-serif;
    /*font-style: italic;*/
    font-size: 2.5rem;
    font-weight: bold;
    padding: 0 2rem;
  }

  main {
    margin: 0;
    padding: 0;
  }
</style>
