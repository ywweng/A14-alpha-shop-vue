<template>
  <div class="form-section">
    <div class="form-title">寄送地址</div>
    <div class="row-container name-container">
      <div class="form-item salutation">
        <label for="salutation">稱謂</label><br />
        <div class="select-container">
          <select name="salutation">
            <option>先生</option>
            <option>女士</option>
          </select>
        </div>
      </div>
      <div class="form-item name">
        <label for="name">姓名</label><br />
        <input type="text" name="name" placeholder="請輸入姓名" />
      </div>
    </div>
    <div class="row-container contact-container">
      <div class="form-item phone">
        <label for="phone" class="title">電話</label><br />
        <input
          type="text"
          id="phone"
          name="phone"
          placeholder="請輸入行動電話"
        />
      </div>
      <div class="form-item email">
        <label for="email" class="title">Email</label><br />
        <input
          type="text"
          id="email"
          name="email"
          placeholder="請輸入電子郵件"
        />
      </div>
    </div>
    <div class="row-container residence-container">
      <div class="form-item county">
        <label for="county" class="title">縣市</label><br />
        <div class="select-container">
          <select id="county" name="county">
            <option>新北市</option>
            <option>台北市</option>
            <option>桃園市</option>
            <option>台中市</option>
            <option>台南市</option>
            <option>高雄市</option>
          </select>
        </div>
      </div>
      <div class="form-item address">
        <label for="address" class="title">地址</label><br />
        <input
          type="text"
          id="address"
          name="address"
          placeholder="請輸入地址"
        />
      </div>
    </div>
  </div>
</template>

<style>
.form-title {
  margin: 1.5rem 0;
  font-size: 1.5rem;
}

label {
  display: inline-block;
  margin-bottom: 8px;
  font-size: 12px;
  font-weight: 700;
  color: #808080;
}
input,
select {
  height: 40px;
  width: 100%;
  border: 1px solid #4a4a4a;
  font-size: 12px;
  color: #999999;
  padding: 12px 16px;
  border-radius: 4px;
  background: transparent;
}
input[type='radio'] {
  padding: unset;
  height: 20px;
  width: 20px;
  -webkit-appearance: none;
  border-radius: 50%;
}
select {
  -webkit-appearance: none;
}

.row-container {
  display: grid;
  grid-auto-flow: column;
  grid-gap: 30px;
  margin-bottom: 1.5rem;
}

.select-container {
  position: relative;
}

.select-container::after {
  content: '\25BE';
  position: absolute;
  top: 50%;
  right: 18px;
  transform: translateY(-50%);
}
</style>
