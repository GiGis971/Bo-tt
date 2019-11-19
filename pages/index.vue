<template>
  <div>
    <section v-for="(product, i) in products" :key="i" class="mb-5">
      <div class="container">
        <div class="row">
          <div class="col">
            <h2 class="mb-3">{{ product.categoryName }}</h2>
            <ProductList :products="product.collection" class="mb-5" />
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import ProductList from '~/components/ProductList'

export default {
  components: {
    ProductList
  },
  data() {
    return {
      products: [
        {
          categoryName: 'Just Booked',
          slug: 'just-booked',
          collection: []
        },
        {
          categoryName: 'Featured experiences',
          slug: 'featured-experiences',
          collection: []
        }
      ]
    }
  },
  mounted() {
    const products = require('~/api/products.json')
    this.products.forEach((category) => {
      category.collection = products.filter(
        (product) => category.slug === product.category
      )
    })
  }
}
</script>

<style>
body,
* {
  font-family: CircularStd, -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, 'Noto Sans', sans-serif,
    'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
}
.color-gray {
  color: #acacac;
}
</style>
