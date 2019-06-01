<script>
  import Product from "./Product.svelte";
  import Button from "./Button.svelte";
  import Cart from "./Cart.svelte";

  let title = "";
  let price = 0;
  let description = "";
  let products = [];
  let cartItems = [];

  function setTitle(event) {
    title = event.target.value;
  }

  function createProduct() {
    let newProduct = {
      title: title,
      price: price,
      description: description
    };
    products = products.concat(newProduct);
  }

  function addToCart(event) {
    let selectedTitle = event.detail;
    cartItems = cartItems.concat({
      ...products.find(prod => prod.title === selectedTitle)
    });

    console.log(cartItems);
  }
</script>

<style>
  section {
    width: 30rem;
    margin: auto;
    margin-top: 2rem;
  }

  label,
  input,
  textarea {
    width: 100%;
  }
</style>

<section>
  <Cart items={cartItems} />
</section>

<hr />

<section>
  <div>
    <label for="title">Title</label>
    <input type="text" name="" id="title" value={title} on:input={setTitle} />
  </div>
  <div>
    <label for="price">Price</label>
    <input type="number" name="" id="price" bind:value={price} />
  </div>
  <div>
    <label for="description">Description</label>
    <textarea id="description" rows="3" bind:value={description} />
  </div>
  <Button on:click={createProduct}>Create Product</Button>
</section>

<section>
  {#if products.length === 0}
    <p>No product added yet!</p>
  {:else}
    {#each products as product}
      <Product
        productTitle={product.title}
        productPrice={product.price}
        productDescription={product.description}
        on:addcart={addToCart} />
    {/each}
  {/if}
</section>
