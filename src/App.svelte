<script>
  import { onDestroy } from 'svelte';
  import countStore from './stores/count.store';
  setTimeout(() => {
    countStore.set(100);
  }, 2000);

  setTimeout(() => {
    countStore.update((n) => {
      return n * 100;
    });
  }, 3000);

  const unsub = countStore.subscribe((n) => {
    console.log('count store', n);
  });
  onDestroy(() => {
    unsub();
  });

  function add() {
    countStore.update((n) => {
      return n + 1;
    });
  }

  function minus() {
    countStore.update((n) => {
      return n - 1;
    });
  }
</script>

<h1>{$countStore}</h1>

<input type="text" bind:value={$countStore} />
<div>
  <button on:click={add}>+</button>
  <button on:click={minus}>-</button>
</div>
