<script>
  import Badge from "@smui-extra/badge";
  import Icon from "@smui/icon-button";

  export let count;
</script>

<div class="cart">
  <Badge>
    <Icon class="material-icons">shopping_cart</Icon>
    {count()}
  </Badge>
  <span>Carrito</span>
</div>

<style>
  .cart {
    margin-top: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
</style>
