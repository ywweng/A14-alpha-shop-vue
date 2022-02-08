<template>
  <div class="stepper-container">
    <div
      class="stepper"
      :class="{ active: currentStep > 1, checked: currentStep > 1 }"
    >
      <div class="circle"></div>
      <div class="label">寄送地址</div>
    </div>
    <div
      class="stepper"
      :class="{ active: currentStep >= 2, checked: currentStep === 3 }"
    >
      <div class="circle"></div>
      <span class="stepper-connect"></span>
      <div class="label">運送方式</div>
    </div>
    <div class="stepper" :class="{ active: currentStep === 3 }">
      <div class="circle"></div>
      <span class="stepper-connect"></span>
      <div class="label">付款資訊</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    currentStep: {
      type: Number,
      required: true,
    },
  },
}
</script>

<style>
.stepper-container {
  display: flex;
  justify-content: space-between;
  margin: 3rem 0;
}

.stepper {
  position: relative;
  display: flex;
  line-height: 32px;
}

.circle {
  height: 32px;
  width: 32px;
  border: 1px solid #afb1bd;
  border-radius: 23px;
}

.stepper:nth-child(1) .circle::after {
  content: '1';
  font-weight: bold;
}

.stepper:nth-child(2) .circle::after {
  content: '2';
  font-weight: bold;
}
.stepper:nth-child(3) .circle::after {
  content: '3';
  font-weight: bold;
}

.stepper .circle {
  margin: 0 0.5rem 0 0;
  text-align: center;
  justify-content: center;
}

.stepper .circle::after {
  color: #afb1bd;
}

.stepper:first-child .circle {
  background-color: #2a2a2a;
}
.stepper:first-child .circle::after {
  background-color: #2a2a2a;
  color: white;
}

.stepper .stepper-connect {
  position: absolute;
  top: 16px;
  right: 110%;
  width: 4rem;
  height: 2px;
  background-color: #afb1bd;
}

.stepper.active .circle {
  border-color: #2a2a2a;
}

.stepper.active .circle::after {
  color: #2a2a2a;
}

.stepper.active .stepper-connect {
  background-color: #2a2a2a;
}

.stepper.checked .circle {
  background-color: #2a2a2a;
}
.stepper.checked .circle::after {
  content: url('./../assets/checked.png');
}
</style>
