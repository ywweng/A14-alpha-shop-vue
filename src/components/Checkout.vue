<template>
  <div>
    <h1>結帳</h1>
    <div class="stepper-container">
      <div class="stepper">
        <div class="circle checked"></div>
        <div class="label">寄送地址</div>
      </div>
      <div class="stepper">
        <div class="circle"></div>
        <span class="stepper-connect"></span>
        <div class="label">運送方式</div>
      </div>
      <div class="stepper">
        <div class="circle"></div>
        <span class="stepper-connect"></span>
        <div class="label">付款資訊</div>
      </div>
    </div>
    <div class="form-panel">
      <CheckoutAddress class="form-section" />
      <CheckoutDelivery class="form-section" />
      <CheckoutPayment class="form-section" />
    </div>
    <div class="control-btn">
      <button class="previous-btn" disabled>← 上一步</button>
      <button class="next-btn">下一步 ➝</button>
    </div>
  </div>
</template>

<script>
import CheckoutAddress from './CheckoutAddress.vue'
import CheckoutDelivery from './CheckoutDelivery.vue'
import CheckoutPayment from './CheckoutPayment.vue'

export default {
  name: 'Checkout',
  components: {
    CheckoutAddress,
    CheckoutDelivery,
    CheckoutPayment,
  },
}
</script>

<style>
.form-section {
  outline: 2px solid yellow;
}
</style>
