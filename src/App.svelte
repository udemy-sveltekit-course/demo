<script>
  const url = 'https://zenquotes.io/api/random';
  let promiseQuote = getQuote();
  async function getQuote() {
    const response = await fetch(url);
    const [quote] = await response.json();
    return quote;
  }

  function refreshQuote() {
    promiseQuote = getQuote();
  }
</script>

<h1>Quotes</h1>

{#await promiseQuote}
  <h2>Awaiting Promise</h2>
{:then quote}
  <h2>{quote.q}</h2>
  <h3>{quote.a}</h3>
{:catch e}
  <h2>{e.message}</h2>
{/await}
<button on:click={refreshQuote}>New Quote</button>
