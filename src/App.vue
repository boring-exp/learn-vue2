<template>
  <div id="app">
    <el-button>这是第一次使用vue框架创建的button</el-button>
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your First Vue Day!"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
