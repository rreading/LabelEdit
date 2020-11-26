<template>
  <div id="app">
    <LabelEdit placeholder="something" :text="text" @updateText="textUpdateCallback" />
  </div>
</template>

<script>
import LabelEdit from './components/LabelEdit.vue'

export default {
  name: 'App',
  components: {
    LabelEdit,
  },
  data() {
    return {
      text: '安徒生童话',
    }
  },
  methods: {
    textUpdateCallback(val) {
      console.log('更新后的文本：' + val)
      window.alert('更新后的文本：' + val)
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
