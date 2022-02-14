<template>
  <div id="app">
    <div class="checkout-title">結帳</div>
    <div id="left-container">
      <Stepper :current-step="currentStep" />
      <div class="form-panel">
        <CheckoutAddress class="form-section" v-if="currentStep === 1" />
        <CheckoutDelivery
          class="form-section"
          @update-delivery-fee="updateDeliveryFee"
          v-else-if="currentStep === 2"
        />
        <CheckoutPayment class="form-section" v-else />
      </div>
      <div class="control-btn">
        <button
          class="previous-btn"
          :disabled="currentStep === 1"
          @click.stop.prevent="prevStep"
        >
          ← 上一步
        </button>
        <button class="next-btn" v-if="currentStep === 3">確認下單</button>
        <button class="next-btn" v-else @click.stop.prevent="nextStep">
          下一步 ➝
        </button>
      </div>
    </div>
    <div id="right-container">
      <div class="cart-panel">
        <div class="cart-title">購物籃</div>
        <CartItemCard @update-products="handleProducts" />
      </div>
      <div class="cart-shipping">
        <span>運費</span
        ><span class="shipping">{{ deliveryFee | priceFormat }}</span>
      </div>
      <div class="cart-total">
        <span>小計</span><span>{{ total | priceFormat }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import Stepper from './components/Stepper.vue'
import CheckoutAddress from './components/CheckoutAddress.vue'
import CheckoutDelivery from './components/CheckoutDelivery.vue'
import CheckoutPayment from './components/CheckoutPayment.vue'
import CartItemCard from './components/CartItemCard.vue'
import { priceFormat } from './utils/mixins'

export default {
  name: 'App',
  components: {
    Stepper,
    CheckoutAddress,
    CheckoutDelivery,
    CheckoutPayment,
    CartItemCard,
  },
  data() {
    return {
      currentStep: 1,
      deliveryFee: 0,
      products: [],
      total: 0,
    }
  },
  mixins: [priceFormat],
  methods: {
    nextStep() {
      this.currentStep++
    },
    prevStep() {
      this.currentStep--
    },
    updateDeliveryFee(fee) {
      this.deliveryFee = fee
      this.calculatedTotal()
    },
    handleProducts(products) {
      this.products = products
    },
    calculatedTotal() {
      let total = 0
      this.products.forEach((product) => {
        let productsTotal = product.count * product.price
        total += productsTotal
      })
      this.total = this.deliveryFee + total
    },
  },
  filters: {
    confirmed() {
      if (this.currentStep === 3) return '確認下單'
    },
  },
  watch: {
    products: {
      handler: function () {
        this.calculatedTotal()
      },
      deep: true,
    },
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

/* left container */

#left-container {
  grid-column: 1 / 7;
}
.form-panel {
  height: 20rem;
}

.control-btn {
  display: flex;
  justify-content: space-between;
  width: 100%;
  padding: 1.5rem 0;
  border-top: 1px solid #e6e6eb;
  position: relative;
  bottom: -8%;
}

.previous-btn {
  border: none;
  background: none;
  margin-right: 40%;
  cursor: pointer;
}

.previous-btn[disabled] {
  display: block;
  visibility: hidden;
}

.next-btn {
  flex: 1;
  min-width: max-content;
  height: 46px;
  border: none;
  border-radius: 8px;
  background: #f67599;
  color: white;
  cursor: pointer;
}

/* left container end */

#right-container {
  grid-column: 8 / 13;
  margin-top: 5rem;
  width: 100%;
  height: fit-content;
  padding: 1.5rem 1.5rem 0 1.5rem;
  border: 1px solid #f0f0f5;
  border-radius: 8px;
  margin-top: 20%;
}

.item-card {
  outline: 2px solid green;
}

.cart-title {
  margin-bottom: 1rem;
  font-size: 18px;
  font-weight: 700;
}

.cart-shipping,
.cart-total {
  display: flex;
  justify-content: space-between;
  padding: 1rem 0 2rem 0;
  border-top: 1px solid #f0f0f5;
}

.shipping,
.total {
  font-weight: 700;
}
</style>
