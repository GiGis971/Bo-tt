<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col order-1 order-md-0 mb-5">
          <h1 class="font-weight-bold pb-1">{{ product.name }}</h1>
          <span class="price h2 text-warning mb-2 d-block font-weight-bold">
            EUR {{ product.amount }}
          </span>
          <div class="custom-border d-block w-100"></div>
          <p style="white-space: pre-line">
            {{ product.description }}
          </p>
          <p class="text-secondary">{{ product.excerpt }}</p>
          <div class="CTA d-flex">
            <div class="quantity mr-3">
              <QuantitySelector :default="1" v-model="selected.quantity" />
            </div>
            <button
              @click="addToCart(product)"
              class="btn btn-warning text-white"
            >
              ADD TO CART
            </button>
          </div>
        </div>
        <div class="col order-0 order-md-1 mb-5">
          <img
            :src="`${image_base}/440/830${product.image}/${image_cache_lock}`"
            :alt="product.name"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import QuantitySelector from '~/components/QuantitySelector'
export default {
  components: {
    QuantitySelector
  },
  data() {
    return {
      product: {},
      image_base: 'https://loremflickr.com/',
      image_cache_lock: '?lock=30976',
      selected: {
        quantity: null
      }
    }
  },
  mounted() {
    const products = require('~/api/products.json')
    const productId = this.$route.params.id
    this.product = products.find((p) => parseFloat(productId) === p.id)
  },
  methods: {
    addToCart(product) {
      if (this.selected.quantity <= 0) return false
      this.$eventBus.$emit('CartNewItem', {
        product,
        quantity: this.selected.quantity
      })
    }
  }
}
</script>

<style>
.custom-border {
  background-color: rgba(254, 189, 23, 0.1);
  height: 13px;
}
</style>
