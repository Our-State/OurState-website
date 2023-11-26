<svelte:head>
  <!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-9EG14MZYZM"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-9EG14MZYZM');
</script>
</svelte:head>

<script lang="ts">
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
        >Make a Bill</button
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

  {#if page == Page.Home}
    <Home on:legislature={() => (page = Page.Legislature)} />
  {:else if page == Page.Legislature}
    <Legislature />
  {:else if page == Page.Recent}
    <Recent />
  {:else if page == Page.Bill}
    <Bill />
  {/if}

  {#if isSignedIn}
    <script>
      console.log("OOGA BOOGA");
    </script>
  {/if}
</main>

<style>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,400;1,600&family=Titillium+Web:ital,wght@0,300;1,400&display=swap');
  button {
    padding-left: 1rem;
    padding-right: 1rem;
    font-size: 16px;
    border: none;
    color: #fffff4;
    background: #000;
    cursor: pointer;
    border-radius: 50px;
    height: 2rem;
  }

  .signIn {
    margin-left: 2rem;
  }

  button:hover {
    background: #fff;
    color: #000;
  }

  nav {
    height: 80px;
    background: #000;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-left: 10%;
    padding-right: 5%;
  }

  .logo {
    color: #fffff4;
    font-family: "Titillium Web", sans-serif;
    font-style:italic;
    font-size: 2.5rem;
    font-weight: bold;
    font-style: italic;
    padding: 0 2rem;
  }
</style>
