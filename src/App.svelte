<script>
  import { fade, fly } from 'svelte/transition';

  import EmojiDisplay from './EmojiDisplay.svelte';
  import EmojiDescription from './EmojiDescription.svelte';
  import Button from './Button.svelte';

  let isLoaded = false;
  let currentEmoji = '😊';
  const emojis = ['😢', '😠', '🚀', '👩‍🚀', '🐈'];
  let m = { x: 0, y: 0 };

  const randomizeEmoji = () => {
    return emojis[Math.floor(Math.random() * emojis.length)];
  };

  const handleRandomButton = () => {
    currentEmoji = randomizeEmoji();
  };

  const handleMouseMove = (e) => {
    m.x = e.clientX;
    m.y = e.clientY;
  };

  setTimeout(() => {
    isLoaded = true;
  }, 3000);
</script>

<svelte:head>
  <link href="/terminal.min.css" rel="stylesheet" />
</svelte:head>

<div class="container" on:mousemove={handleMouseMove}>
  <p>The mouse position: {m.x} x {m.y}</p>
  <h1>Emoji Randomizer</h1>
  <h3>Available Emoji</h3>
  <ul>
    {#each emojis as emoji}
      <li>{emoji}</li>
    {/each}
  </ul>
  {#if isLoaded === true}
    <div in:fly={{ y: 200, duration: 2000 }} out:fade>
      <EmojiDisplay {currentEmoji} />
      <EmojiDescription />
      <Button on:click={handleRandomButton} title={'🔁 Randomize'} />
    </div>
  {:else}
    <h2>Loading...</h2>
  {/if}

  <Button
    on:click={() => (isLoaded = !isLoaded)}
    title={`Toggle : ${isLoaded}`}
  />
</div>

<style>
  div {
    margin: 2em;
  }
</style>
