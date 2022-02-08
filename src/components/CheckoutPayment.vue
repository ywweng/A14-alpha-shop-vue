<template>
  <div class="form-section">
    <div class="form-title">付款資訊</div>
    <div class="row-container">
      <div class="form-item">
        <label for="holder" class="title">持卡人姓名</label><br />
        <input type="text" id="holder" name="holder" placeholder="John Doe" />
      </div>
    </div>
    <div class="row-container">
      <div class="form-item">
        <label for="card-number" class="title">卡號</label><br />
        <input
          type="text"
          id="card-number"
          name="card-number"
          maxlength="12"
          placeholder="1111 2222 3333 4444"
        />
      </div>
    </div>
    <div class="row-container valid-container">
      <div class="form-item">
        <label for="valid-thru" class="title">有效期限</label><br />
        <input type="month" id="valid-thru" name="valid-thru" value="2021-12" />
      </div>
      <div class="form-item">
        <label for="cvc" class="title">CVC/CCV</label><br />
        <input type="password" id="cvc" name="cvc" maxlength="3" />
      </div>
    </div>
  </div>
</template>
