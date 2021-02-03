<script>
  import {} from 'os';

  let description = '';
  $: characters = description.length;
  $: words = description.split(' ').length;

  $: if (description.length > 10) {
    console.log('------');
    console.log('Description : ', description);
  }

  const handleSubmit = (event) => {
    console.log('form submitted. thanks!');
    description = '';
  };
</script>

<div class="form-group">
  <p>{description}</p>
  <form on:submit|preventDefault={handleSubmit}>
    <textarea bind:value={description} rows="7" />
    <button type="submit">Save</button>
  </form>
  <p>Characters count : {characters}</p>
  <p>Words count : {words}</p>
</div>

<style>
  div {
    margin: 1em 0;
  }
</style>
