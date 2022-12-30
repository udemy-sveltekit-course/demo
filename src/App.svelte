<script>
  import { onDestroy } from 'svelte';
  import countStore from './stores/count.store';
  setTimeout(() => {
    countStore.set(100);
  }, 2000);

  setTimeout(() => {
    countStore.multipleBy(100);
  }, 3000);

  const unsub = countStore.subscribe((n) => {
    console.log('count store', n);
  });
  onDestroy(() => {
    unsub();
  });

  function add() {
    countStore.addOne();
  }

  function minus() {
    countStore.minusOne();
  }
</script>

<h1>{$countStore}</h1>

<input type="text" bind:value={$countStore} />
<div>
  <button on:click={add}>+</button>
  <button on:click={minus}>-</button>
</div>
