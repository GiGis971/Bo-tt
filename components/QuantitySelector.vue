<template>
  <div id="QteBtns">
    <button @click="handleDecrement">-</button>
    <div class="quantity">{{ quantity }}</div>
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

<style scoped lang="scss">
#QteBtns {
  background-color: rgba(229, 229, 229, 0.5);
  border-radius: 3px;
  display: flex;
  flex-wrap: nowrap;
  flex-direction: row;
  padding: 1px 4px;
  align-items: center;
  justify-content: center;
  button {
    background: white;
    font-size: 1.3em;
    border: 1px solid #e5e5e5;
    border-radius: 2px;
  }
  .quantity {
    padding: 8px;
  }
}
</style>
