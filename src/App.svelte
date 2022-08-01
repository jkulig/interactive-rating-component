<script>
  import Card from './lib/Card.svelte';
  import Feedback from './lib/Feedback.svelte';
  import Summary from './lib/Summary.svelte';

  let summary = false;
  
  function onSuccess() {
    summary = true;
  }

</script>

<svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="true">
    <link href="https://fonts.googleapis.com/css2?family=Overpass:wght@400;700&display=swap" rel="stylesheet">
    <link rel="icon" type="image/png" sizes="32x32" href="/public/favicon-32x32.png">
</svelte:head>

<main>
  <Card summary={summary}>
    {#if !summary}
        <Feedback on:success={onSuccess}></Feedback>
      {:else}
        <Summary></Summary>
    {/if}
  </Card>
</main>

<style>
  main {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
</style>
