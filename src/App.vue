<template>
  <div id="app">
    <div class="checkout-title">結帳</div>
    <Checkout id="left-container" />
    <Cart id="right-container" />
  </div>
</template>

<script>
import Checkout from './components/Checkout.vue'
import Cart from './components/Cart.vue'

export default {
  name: 'App',
  components: {
    Checkout,
    Cart,
  },
}
</script>

<style>
/* reset css */
*,
*:before,
*:after {
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}

body,
h1,
h2,
h3,
h4,
h5,
h6,
ol,
ul,
menu {
  margin: 0;
  padding: 0;
  font-weight: normal;
}

ul,
li {
  list-style-type: none;
}

a {
  cursor: pointer;
}

a:link,
a:visited {
  color: inherit;
  text-decoration: none;
}

table {
  border: none;
  border-spacing: 0;
  border-collapse: collapse;
}

th,
td {
  text-align: initial;
}

button {
  background-color: transparent;
  border: 0;
  cursor: pointer;
}
/* reset css end */

#app {
  width: 85%;
  height: 100%;
  margin: 5rem auto;
  display: grid;
  grid-template-columns: repeat(12, minmax(min-content, 1fr));
}

.checkout-title {
  font-size: 2rem;
  font-weight: 700;
}

#left-container {
  grid-column: 1 / 7;
}

#right-container {
  grid-column: 8 / 13;
  outline: 2px solid blue;
  margin-top: 5rem;
}
</style>
