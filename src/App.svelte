<!-- untuk menampung code javascript -->
<script>
  import EmojiDisplay from "./components/EmojiDisplay.svelte";
  import EmojiDescription from "./components/EmojiDescription.svelte";
  import Button from "./components/Button.svelte";
  import {fade, fly} from "svelte/transition";

  let isLoaded = false;
  let currentEmoji = "😁";
  const emojis = ["🤣", "🙈", "👻", "🚀"];
  let m = { x: 0, y: 0 };

  function randomizeEmoji() {
    return emojis[Math.floor(Math.random() * emojis.length)];
  }

  function handleRandomButton() {
    currentEmoji = randomizeEmoji();
  }

  // function loading
  setTimeout(function () {
    isLoaded = true;
  }, 2000);

  function handleMouseMove(event) {
    m.x = event.clientX;
    m.y = event.clientY;
  }
</script>

<!-- Membuat css -->
<style>
  div {
    margin: 2em;
  }
</style>

<svelte:head>
  <link rel="stylesheet" href="terminal.min.css" />
</svelte:head>

<!-- html -->
<div class="container" on:mousemove={handleMouseMove}>
  <p>The mouse position: {m.x} x {m.y}</p>
  <h1>Randomize Emoji</h1>
  <ul>
    {#each emojis as emoji}
      <li>{emoji}</li>
    {/each}
  </ul>
  {#if isLoaded === true}
    <div in:fly={{ y: 200, duration: 2000}} out:fade>
      <EmojiDisplay {currentEmoji} />
      <EmojiDescription />
      <Button on:click={handleRandomButton} title={'🔄 Randomize'} />
    </div>
  {:else}
    <h2>Please Wait...</h2>
  {/if}

  <Button title={'Toggle'} on:click={() => (isLoaded = !isLoaded)} />
</div>
