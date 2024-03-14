<script>
    import Button from '@smui/button';
    import Badge from '@smui-extra/badge';
    import Icon from '@smui/icon-button';
    import { Label } from '@smui/button';

    let cart = [];
    const products = [
      { id: 1, name: 'Producto 1', quantity: 0 },
      { id: 2, name: 'Producto 2', quantity: 0 },
      { id: 3, name: 'Producto 3', quantity: 0 },
    ];
  
    const addToCart = (productId) => {
      const productIndex = cart.findIndex((p) => p.id === productId);
      if (productIndex > -1) {
        cart[productIndex].quantity += 1;
        cart = cart
      } else {
        const product = products.find((p) => p.id === productId);
        cart = [...cart, { ...product, quantity: 1 }];
      }
    };
  
    const removeFromCart = (productId) => {
      const productIndex = cart.findIndex((p) => p.id === productId);
      if (productIndex > -1) {
        if (cart[productIndex].quantity > 1) {
          cart[productIndex].quantity -= 1;
        } else {
          cart = cart.filter((p) => p.id !== productId);
        }
      }
    };
  
    const totalItemsInCart = () => {
      return cart.reduce((acc, curr) => acc + curr.quantity, 0);
    };
  </script>
  
  <div class="container">
    <h1>Tienda</h1>
    <div class="products">
      {#each products as product}
        <div class="product">
          <span>{product.name}</span>
          <Button on:click={() => addToCart(product.id)}>+</Button>
          <Button on:click={() => removeFromCart(product.id)}>-</Button>
        </div>
      {/each}
    </div>
    <div class="cart">
      <Badge  position='middle' color='primary' use={totalItemsInCart()}>
        <Icon class="material-icons">shopping_cart</Icon>
      </Badge>
      <span>Carrito { totalItemsInCart() }</span>
    </div>
  </div>
  
  <style >

    .container {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 20px;
    }
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
    .cart {
      margin-top: 20px;
      display: flex;
      align-items: center;
      gap: 10px;
    }
  </style>
  