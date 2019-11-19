<template>
  <div class="d-flex flex-wrap">
    <button @click="handleDecrement">-</button>
    <div>{{ quantity }}</div>
    <button @click="handleIncrement">+</button>
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
      quantity: null
    }
  },
  mounted() {
    this.quantity = this.default
    this.$emit('input', this.quantity)
  },
  methods: {
    handleDecrement() {
      this.quantity = this.quantity === 1 ? this.quantity : this.quantity - 1
      this.$emit('input', this.quantity)
    },
    handleIncrement() {
      this.quantity++
      this.$emit('input', this.quantity)
    }
  }
}
</script>

<style scoped lang="scss"></style>
