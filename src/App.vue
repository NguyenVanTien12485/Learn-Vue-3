<template>
  <div id="app">
    <Headers/>
    <Todos/>
  </div>
</template>

<script>
import Headers from './components/Header'
import Todos from './components/Todos'
export default {
  name: "App",
  components: {
    Headers,
    Todos,
  }
}
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  #app {
    font-family: Arial, Helvetica, sans-serif;
  }
</style>