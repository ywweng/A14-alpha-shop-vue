<template>
  <div>
    <div class="cart-panel">
      <div class="cart-title">購物籃</div>
      <CartItemCard class="item-card" v-for="card in 5" :key="card.index" />
    </div>
    <div class="cart-shipping">
      <span>運費</span><span class="shipping">免費</span>
    </div>
    <div class="cart-total">
      <span>小計</span><span class="total">$5,298</span>
    </div>
  </div>
</template>

<script>
import CartItemCard from './CartItemCard.vue'

export default {
  components: {
    CartItemCard,
  },
}
</script>

<style>
.item-card {
  outline: 2px solid green;
}
</style>
