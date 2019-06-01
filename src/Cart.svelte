<script>
  export let items = [];

  $: cartTotal = items.reduce((sum, currTotal) => {
    return sum + currTotal.price;
  }, 0);
</script>

<style>
  ul {
    list-style: none;
    margin: 1rem;
    padding: 0;
  }
  li {
    margin: 0.5 rem 0.25rem;
    padding: 0.5rem;
    border: 1px solid lightgray;
  }

  h1 {
    font-size: 1.5rem;
    margin: 1rem;
  }
</style>

{#if items.length === 0}
  <p>No items added yet!!</p>
{:else}
  <ul>
    {#each items as item}
      <li>{item.title} - ₹{item.price} </li>
    {/each}
  </ul>
  <h1>TOTAL: ₹{cartTotal}</h1>
{/if}
