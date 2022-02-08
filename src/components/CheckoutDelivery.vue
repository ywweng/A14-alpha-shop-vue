<template>
  <div class="form-section">
    <div class="form-title">運送方式</div>
    <div class="delivery-container">
      <input type="radio" id="standard-delivery" name="delivery" checked />
      <div class="delivery-item">
        <label for="standard-delivery">
          <div class="delivery-name">標準運送</div>
          <div class="delivery-day">約3~7個工作天</div>
          <div class="delivery-fee">免費</div>
        </label>
      </div>
    </div>
    <div class="delivery-container">
      <input type="radio" id="DHL-delivery" name="delivery" />
      <div class="delivery-item">
        <label for="DHL-delivery">
          <div class="delivery-name" id="DHL-delivery">DHL 貨運</div>
          <div class="delivery-day">48小時內送達</div>
          <div class="delivery-fee">$500</div>
        </label>
      </div>
    </div>
  </div>
</template>

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
.delivery-day {
  font-size: 12px;
  font-weight: normal;
}
.delivery-fee {
  position: absolute;
  top: 13px;
  right: 13px;
  font-weight: normal;
}
#DHL-delivery {
  font-weight: 700;
}
</style>
