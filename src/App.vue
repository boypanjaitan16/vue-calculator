<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" style="width: 100px;">
    <p><br/></p>
    <MyForm/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import MyForm from './components/MyForm';

export default {
  name: 'App',
  components: {
    // HelloWorld,
    MyForm
  }
}
</script>

<style>
@import "https://stackpath.bootstrapcdn.com/bootstrap/4.1.2/css/bootstrap.min.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
