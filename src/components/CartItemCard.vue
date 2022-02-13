<template>
  <div>
    <div class="item-container" v-for="product in products" :key="product.id">
      <div class="item-img">
        <img :src="product.image" alt="" />
      </div>
      <div class="item-content">
        <div class="item-title">{{ product.name }}</div>
        <div class="item-count">
          <button
            class="count-btn"
            id="count-minus"
            @click="countMinus(product)"
          >
            -
          </button>
          <span class="count">{{ product.count }}</span>
          <button class="count-btn" id="count-plus" @click="product.count++">
            +
          </button>
        </div>
        <div class="item-price">{{ product.price | priceFormat }}</div>
      </div>
    </div>
  </div>
</template>

<script>
const products = [
  {
    id: 1,
    name: '破壞補丁修身牛仔褲',
    image: require('./../assets/item1.png'),
    price: 3999,
    count: 1,
  },
  {
    id: 2,
    name: '刷色牛仔褲',
    image: require('./../assets/item2.png'),
    price: 1299,
    count: 1,
  },
]

export default {
  data() {
    return {
      products: products,
    }
  },
  methods: {
    countMinus(product) {
      if (product.count > 0) {
        product.count--
        this.$emit('update-products', products)
      }
    },
    countPlus(product) {
      product.count++
      this.$emit('update-products', products)
    },
  },
  filters: {
    priceFormat(price) {
      return '$' + price.toString().replace(/(\d)(?=(\d{3})+(\.\d+)?$)/g, '$1,')
    },
  },
  created() {
    this.$emit('update-products', products)
  },
}
</script>

<style>
.item-container {
  position: relative;
  display: flex;
  justify-content: flex-start;
  margin-bottom: 2rem;
}

.item-content {
  align-items: flex-start;
  justify-content: flex-start;
}

.item-img {
  width: 100px;
  height: 100px;
  margin-right: 1.25rem;
}

.item-img img {
  object-fit: fill;
}

.item-content .item-title {
  margin-bottom: 1rem;
}

.item-count {
  display: flex;
  justify-content: space-between;
  width: 100px;
}

.count-btn {
  width: 26px;
  height: 27px;
  border: none;
  border-radius: 50%;
  background: #f0f0f5;
  cursor: pointer;
  font-size: 1.5rem;
}

.item-price {
  position: absolute;
  top: 0;
  right: 0;
}
</style>
