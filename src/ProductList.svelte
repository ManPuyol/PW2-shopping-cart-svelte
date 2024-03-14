<script>
  import CartCount from './CartCount.svelte';

    import Button from '@smui/button';

    export let products;
    export let addToCart;
    export let removeFromCart;
  </script>

    <div class="products">
      {#each products as product}
        <div class="product">
          <span>{product.name}</span>
          <Button on:click={() => addToCart(product.id)}>+</Button>
          <Button on:click={() => removeFromCart(product.id)}>-</Button>
        </div>
      {/each}
    </div>

<style >
    .products {
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      width: 100%;
    }
    .product {
      display: flex;
      align-items: center;
      gap: 10px;
    }
  </style>

