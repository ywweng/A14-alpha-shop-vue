<template>
  <div>
    <Stepper :current-step="currentStep" />
    <div class="form-panel">
      <CheckoutAddress class="form-section" v-if="currentStep === 1" />
      <CheckoutDelivery class="form-section" v-else-if="currentStep === 2" />
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
      <button
        class="next-btn"
        :disabled="currentStep === 3"
        @click.stop.prevent="nextStep"
      >
        下一步 ➝
      </button>
    </div>
  </div>
</template>

<script>
import Stepper from './Stepper.vue'
import CheckoutAddress from './CheckoutAddress.vue'
import CheckoutDelivery from './CheckoutDelivery.vue'
import CheckoutPayment from './CheckoutPayment.vue'

export default {
  name: 'Checkout',
  components: {
    Stepper,
    CheckoutAddress,
    CheckoutDelivery,
    CheckoutPayment,
  },
  data() {
    return {
      currentStep: 1,
    }
  },
  methods: {
    nextStep() {
      this.currentStep++
    },
    prevStep() {
      this.currentStep--
    },
  },
}
</script>

<style>
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
  bottom: -50px;
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
</style>
