<script>
  import { onMount, onDestroy } from "svelte";

  $: users = [];
  onMount(async () => {
    console.log("Mounted");
    //litmit code
    //    return () =>{
    //        console.log("Destroyed (from onMount)");
    //    }

    const res = await fetch("https://jsonplaceholder.typicode.com/users");
    users = await res.json();
    
  });
  onDestroy(() => {
    console.log("Destroyed");
  });
</script>

<!-- <img src="https://svelte.dev/tutorial/image.gif" alt="img" class=""> -->
{#if fetch.length > 0}
  <ul>
    {#each users as user}
      <li>{user.username}</li>
    {/each}
  </ul>
{/if}

<style>
  img {
    border: 3px solid red;
    padding: 10px;
  }
</style>
