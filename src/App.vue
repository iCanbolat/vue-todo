<template>
<div class="container">
  <ToDo/>
</div>
  
</template>

<script>
import ToDo from './components/ToDo.vue'
import "bootstrap/dist/css/bootstrap.min.css";

export default {
  name: 'App',
  components: {
    ToDo
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
  color: #2c3e50;
  
}
</style>
