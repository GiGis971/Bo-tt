<template>
  <div class="d-flex flex-wrap">
    <button>-</button>
    <div>{{ quantity }}</div>
    <button>+</button>
  </div>
</template>

<script>
export default {
  props: {
    default: {
      type: Number,
      required: false,
      default: 1
    }
  },
  data() {
    return {
      quantity: 1
    }
  }
}
</script>

<style scoped lang="scss"></style>
