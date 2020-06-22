<template>
  <div id="app">
    <Main/>
  </div>
</template>

<script>
import Main from './pages/Main.vue'

export default {
  name: 'app',
  components: {
    Main
  }
}
</script>

<style>
/*Import local font: huninn*/
@font-face {
  font-family: 'jf-openhuninn-1.1';
  src: url('./assets/fonts/jf-openhuninn-11.eot');
  src: url('./assets/fonts/jf-openhuninn-11.eot?#iefix') format('embedded-opentype'),
       url('./assets/fonts/jf-openhuninn-11.woff2') format('woff2'),
       url('./assets/fonts/jf-openhuninn-11.woff') format('woff'),
       url('./assets/fonts/jf-openhuninn-11.svg#jf-openhuninn-1.1') format('svg');
  font-weight: normal;
  font-style: normal;
}

* {
  font-family: 'jf-openhuninn-1.1', 'Avenir', 'Helvetica', 'Arial', sans-serif !important;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 60px;
  height: 100vh;
}

html body {
  background-color: #d9d9d9;
}
</style>
