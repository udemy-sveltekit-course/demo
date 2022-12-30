<script>
  import exStore, { store1 } from './stores/ex.store';
  setTimeout(() => {
    store1.set(100);
  }, 2000);
</script>

<h1>{$exStore}</h1>
