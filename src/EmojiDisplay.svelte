<script>
  export let currentEmoji;

  let currentButton = 'button1';

  const handleButtonChange = (e) => {
    currentButton = e.target.name;
  };
</script>

<div>{currentEmoji}</div>
<button
  class="btn"
  class:btn-primary={currentButton === 'button1'}
  name="button1"
  on:click={handleButtonChange}>Button 1</button
>
<button
  class="btn"
  class:btn-primary={currentButton === 'button2'}
  name="button2"
  on:click={handleButtonChange}>Button 2</button
>
<button
  class="btn"
  class:btn-primary={currentButton === 'button3'}
  name="button3"
  on:click={handleButtonChange}>Button 3</button
>

<style>
  div {
    margin: 1em 0;
    font-size: 3em;
  }
</style>
