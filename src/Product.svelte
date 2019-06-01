<script>
  import { createEventDispatcher } from "svelte";
  import Button from "./Button.svelte";

  export let productTitle;
  export let productPrice;
  export let productDescription;

  const dispatch = createEventDispatcher();
  function addToCart() {
    dispatch("addcart", productTitle);
  }
</script>

<style>
  div {
    margin: 1rem 0;
    padding: 1rem;
    border-radius: 5px;
    background-color: white;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  }

  h1 {
    font-size: 1.25rem;
    margin: 0.25rem 0;
  }

  h2 {
    font-size: 1rem;
    margin: 0.25rem 0;
    color: grey;
  }

  p {
    margin: 0.25rem 0;
  }
</style>

<div>
  <h1>{productTitle}</h1>
  <h2>{productPrice}</h2>
  <p>{productDescription}</p>
  <Button on:click={addToCart}>Add to Cart</Button>
</div>
