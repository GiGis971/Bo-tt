<template>
  <div class="d-flex flex-wrap flex-md-nowrap">
    <div
      v-for="(product, i) in products"
      :key="i"
      class="font-weight-lighter product"
    >
      <nuxt-link :to="`/product/${product.id}`" class="text-secondary">
        <img
          :src="`${image_base}/194/290${product.image}/${image_cache_lock}`"
          :alt="product.name"
          class="d-block mb-1 w-100"
        />
        <div class="d-inline-block">
          <span class="price font-weight-bolder"> ${{ product.amount }} </span>
          <span class="name line" style="white-space: pre-line">{{
            product.name
          }}</span>
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    products: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      image_base: 'https://loremflickr.com/',
      image_cache_lock: ''
    }
  }
}
</script>

<style scoped lang="scss">
.product {
  margin-right: 16px;
  &:last-of-type {
    margin-right: 0;
  }
}
</style>
