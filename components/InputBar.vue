<template>
    <input type="text"
           class="input"
           :value="value"
           v-on="listeners">
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: '',
    }
  },
  computed: {
    listeners () {
      return {
        // Pass all component listeners directly to input
        ...this.$listeners,
        // Override input listener to work with v-model
        input: event => this.$emit('input', event.target.value)
      }
    }
  }
}
</script>

<style>
    input[type=text] {
        width: 50%;
        padding: 12px 20px;
        margin: 8px 0;
        box-sizing: border-box;
    }
</style>