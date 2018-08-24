<template>
    <div>
        <ul v-for="(value, name, index) in this.data" :key="index">
            <li v-if="typeof value === 'object'">
                {{name}}
                <fg v-if="typeof value === 'object'" :data=value></fg>
            </li>
            <TextNode v-if="typeof value === 'string'" :name=name v-model="data[name]"></TextNode>
            <NumberNode v-if="typeof value === 'number'" :name=name v-model.number="data[name]"></NumberNode>
            <BooleanNode v-if="typeof value === 'boolean'" :name=name :value=value v-model="data[name]"></BooleanNode>
        </ul>
    </div>
</template>

<script>
import TextNode from './TextNode.vue'
import NumberNode from './NumberNode.vue'
import BooleanNode from './BooleanNode.vue'

export default {
  name: 'fg',
  props: ['data'],
  components: {
      TextNode, NumberNode, BooleanNode
  }
}
</script>

<style scoped>
ul, li {
  text-align: left;
  font-size: 14px;
}
</style>
