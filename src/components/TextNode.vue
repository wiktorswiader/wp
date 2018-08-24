<template>
    <li>
      <label>{{name}} </label><input type="text" :value="value" @input="onInput($event.target)">
    </li>
</template>

<script>

export default {
  name: 'TextNode',
  props: ['name', 'value'],
  methods: {
    onInput(target) {
      this.$emit('input', target.value);
    }
  }
}
</script>

<style scoped>
</style>
