<template>
  <div id="app">
    <test/>
  </div>
</template>

<script>
import He from './components/He'
import test from './components/test'

export default {
  name: 'App',
  components: {
    test
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
  margin-top: 200px;
  display: flex;
  justify-content: center;
}
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
