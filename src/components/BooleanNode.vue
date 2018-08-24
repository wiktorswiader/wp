<template>
    <li>
      <label>{{name}} - {{mutableValue}}</label><input type="checkbox" v-model="mutableValue" @change="$emit('input', $event.target.checked)">
    </li>
</template>

<script>

export default {
  name: 'BooleanNode',
  props: ['name', 'value'],
  data() {
    return {
      mutableValue: JSON.parse(this.value)
    }
  }
}
</script>

<style scoped>
</style>
