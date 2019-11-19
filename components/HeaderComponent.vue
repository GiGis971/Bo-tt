<template>
  <header class="px-5 w-100 d-flex border-bottom py-3">
    <div><LogoComponent /></div>
    <div class="d-flex ml-auto align-items-center border-left pr-5 pl-2">
      <div class="badge badge-pill badge-warning text-white align-self-center">
        0
      </div>
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
  }
}
</script>
