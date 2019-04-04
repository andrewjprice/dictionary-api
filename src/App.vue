<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1 class="h1">Nothing is more permanent than temporary</h1>
    <Input />
  </div>
</template>

<script>
import Input from './components/Input.vue'
require('dotenv').config();
export default {
  name: 'app',
  components: {
    Input
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
  background-color: teal;
}

.h1{
  color: #fff;
  font-weight: bold;
}
</style>
