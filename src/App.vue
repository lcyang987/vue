<template>
  <div id="app">
  	测试
    <cmain></cmain>
  </div>
</template>

<script>
import cmain from './components/Hello'

export default {
  name: 'app',
  components: {
    cmain
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
