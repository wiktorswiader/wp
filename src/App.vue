<template>
  <div id="app">
    <div id="upper">
      <h1>{{title}}</h1>
      <button v-on:click="copyToClipboard">Copy to clipboard</button>
    </div>
    <FormGenerator :data="data"></FormGenerator>
  </div>
</template>

<script>
import FormGenerator from './components/FormGenerator.vue'

export default {
  name: 'app',
  data() {
    return {
      title: 'JSON Editor', 
      data: {}
    }
  },
  components: {
    FormGenerator
  },
  methods: {
    loadData() {
      this.data = window.prebidConfig;
    },
    copyToClipboard() {
      let textNode = document.createElement('textarea');
      textNode.value = JSON.stringify(this.data, null, 2);
      document.body.appendChild(textNode);    
      textNode.select();
      document.execCommand('copy');
      document.body.removeChild(textNode);
    }
  },
  created() {
    this.loadData();
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  width: 600px;
  margin: 0 auto;
  height: 100%;
  min-height: 100%;
  background-color: rgb(231, 231, 235);
  border: 1px solid black;
  font-family: 'Verdana', sans-serif;
}
#upper {
  width: 100%;
  padding: 10px 0;
  background-color: #9aa5b1;
  text-align: center;
}
button {
  padding: 5px;
  border-radius: 4px;
  background-color: #bd1010;
  border: none;
  cursor: pointer;
  color: #ebebeb;
  font-size: 14px;
}
button:hover {
  background-color: #7b0b0b;
}
</style>
