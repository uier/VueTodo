<template>
  <div id="app">
    <Header/>
    <List/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import List from './components/List.vue'

export default {
  name: 'app',
  components: {
    Header, List
  }
}
</script>

<style>
#app {
  font-family: "Avenir", "Helvetica", "Arial", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 60px;
  height: 100vh;
}

html body {
  background: linear-gradient(124deg, #ff240080, #e81d1d80, #e8b71d80, #e3e81d80, #1de84080, #1ddde880, #2b1de880, #dd00f380, #dd00f380);
}
</style>
