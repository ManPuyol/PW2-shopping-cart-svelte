<script>
  import ProductList from './ProductList.svelte';

  import CartCount from './CartCount.svelte';

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
  
    $: totalItemsInCart = () => {
      return cart.reduce((acc, curr) => acc + curr.quantity, 0);
    };
  </script>
  
  <div class="container">
    <h1>Tienda</h1>
<ProductList products={products} {removeFromCart} {addToCart}  ></ProductList>
<CartCount count={totalItemsInCart} ></CartCount>
  </div>
  
  <style >
    .container {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 20px;
    }
  </style>
  