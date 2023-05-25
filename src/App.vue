<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld/>
  <ApplicationForm/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ApplicationForm from './components/ApplicationForm.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    ApplicationForm
  },
  props:{
    // info:object
  }
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
