<template>
  <header class="px-5 w-100 d-flex border-bottom py-3 sticky-top bg-white">
    <div>
      <nuxt-link to="/"><LogoComponent /></nuxt-link>
    </div>
    <div class="d-flex ml-auto align-items-center border-left pr-5 pl-2">
      <div class="badge badge-pill badge-warning text-white align-self-center">
        {{ quantity }}
      </div>
      <span class="px-2 color-gray">$ {{ totalAmount }}</span>
      <span class="px-2 color-gray">Shoping cart</span>
      <img src="~/static/ico-cart.svg" />
    </div>
  </header>
</template>

<script>
import LogoComponent from '~/components/LogoComponent.vue'

export default {
  components: {
    LogoComponent
  },
  data() {
    return {
      cart: [],
      quantity: 0
    }
  },
  computed: {
    totalAmount() {
      if (this.cart.length <= 0) return 0
      return this.cart.reduce((a, r) => parseFloat(a) + parseFloat(r.amount), 0)
    }
  },
  mounted() {
    this.$eventBus.$on('CartNewItem', (e) => {
      this.cart.push({
        quantity: e.quantity,
        ...e.product
      })
      this.quantity += e.quantity
    })
  }
}
</script>
