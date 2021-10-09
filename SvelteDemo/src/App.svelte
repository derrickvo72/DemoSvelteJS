<script>
  import { fade, fly } from "svelte/transition";
  import Lifecycle from "./Lifecycle.svelte";
  import Reactive from "./Reactive.svelte";

  export let name;
 
  let t = "Svelte";
  let src = "https://svelte.dev/tutorial/image.gif";
  let check = "",
    sve = "Event";
  function setSve() {
    check = document.getElementById("compare").value;
    sve = Math.floor(Math.random() * 5);
  }
  let developer = [
    { name: "Jack", level: "fresher" },
    { name: "Karl", level: "Junior" },
    { name: "John", level: "Senior" },
  ];

  const say = {
    action: "Hello everyone !",
  };

  let major = ["developer", "tester", "architectural engineering"];
  setTimeout(() => {
    major = [...major, "pm"];
    say.action="Have a good day !"
    // major.push("pm");
    // major = major ;
  }, 5000);
  let show = false;
</script>

<main>
  <p class="">Props</p>
  <h1>Hello {name}!</h1>
  <h1>And welcome to {t}</h1>
  <hr />
  <p class="">{sve}</p>
  <button on:click={setSve}>Check</button>
  <!-- <button on:click|once={setSve}>Check</button> -->
  <hr />
  <p class="">Condition</p>
  <input id="compare"   placeholder="Enter your number" type="text" />
  <!-- bind:value={check}
  <p>Your choose: {check}</p> -->
  {#if check == ""}
    <!-- <img src={src} alt="win" class=""/> -->
    <p class="">Win or Lose ...</p>
  {:else if check == sve}
    <p transition:fade>Win</p>
  {:else}
    <p in:fly={{ x: 1000, duration: 500 }} out:fly={{ x: -500, duration: 500 }}>
      Lose
    </p>
  {/if}
  <hr />

  <p>Loop</p>
  {#each developer as person, index}
    <p>[{index}] {person.name} - level: {person.level}</p>
  {/each}

  <hr />
  <p>Array and Object</p>
  <p>{say.action}</p>
  {#each major as item, index}
    <p>[{index}]{item}</p>
  {/each}
  <hr />

  <p class="">Lifecycle</p>
  <check>
    <button on:click={() => (show = !show)}>Click me!</button>
    {#if show}
      <Lifecycle />
    {/if}
  </check>
  <hr />
  <p class="">Reactive Declarations and Statements</p>
  <Reactive />
</main>

<style>
  check {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: black;
    text-transform: uppercase;
    font-size: 1em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
