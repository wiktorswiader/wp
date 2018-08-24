<template>
    <li>
      <label>{{name}} </label><input type="number" :value="value" @input="onInput($event.target)">
    </li>
</template>

<script>

export default {
  name: 'NumberNode',
  props: ['name', 'value'],
  data() {
    return {
      previous: null
    }
  },
  methods: {
    onInput(target) {
      if (!this.isNumeric(target.value)) {
        target.value = (target.value === '') ? 0 : this.previous;
      }
      this.previous = target.value;
      this.$emit('input', target.value);
    },
    isNumeric(value) {
      return !isNaN(parseFloat(value)) && isFinite(value);
    }
  },
  created() {
    this.previous = this.value;
  }
}
</script>

<style scoped>
</style>
