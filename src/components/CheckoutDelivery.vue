<template>
  <div class="form-section">
    <div class="form-title">運送方式</div>
    <div
      class="delivery-container"
      v-for="delivery in deliveries"
      :key="delivery.id"
    >
      <input
        type="radio"
        id="standard-delivery"
        name="delivery"
        :checked="delivery.id === 1"
      />
      <div class="delivery-item">
        <label for="standard-delivery">
          <div class="delivery-name">{{ delivery.name }}</div>
          <div class="delivery-days">{{ delivery.days }}</div>
          <div class="delivery-fee">{{ delivery.fee | priceFormat }}</div>
        </label>
      </div>
    </div>
  </div>
</template>

<script>
const deliveries = [
  {
    id: 1,
    name: '標準運送',
    days: '約3~7個工作天',
    fee: 0,
  },
  {
    id: 2,
    name: 'DHL 貨運',
    days: '48小時內送達',
    fee: 500,
  },
]

export default {
  data() {
    return {
      deliveries: deliveries,
    }
  },
  filters: {
    priceFormat(value) {
      if (value === 0) return '免費'
      if (value > 0) return '$' + value
    },
  },
}
</script>

<style>
.delivery-container {
  position: relative;
  display: flex;
  margin-bottom: 1.5rem;
  border: 1px solid #f0f0f5;
  border-radius: 4px;
  height: 60px;
}
.delivery-container:hover {
  border-color: #2a2a2a;
}
.delivery-container input {
  margin: 1.2rem;
  cursor: pointer;
}

input:checked {
  box-shadow: inset 0 0 0 5px #2a2a2a;
}

.delivery-item {
  margin: 11px 0;
}
.delivery-item div {
  color: black;
}
.delivery-name {
  font-size: 14px;
}
.delivery-days {
  font-size: 12px;
  font-weight: normal;
}
.delivery-fee {
  position: absolute;
  top: 13px;
  right: 13px;
  font-weight: normal;
}
</style>
