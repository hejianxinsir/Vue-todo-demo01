<template>
  <div id="app">
    <He/>
  </div>
</template>

<script>
import He from './components/He'

export default {
  name: 'App',
  components: {
    He
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
