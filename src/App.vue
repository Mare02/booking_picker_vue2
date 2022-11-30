<template>
  <div id="app">
    <Navbar/>
    <Page_Template/>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Page_Template from './components/Page_Template.vue';

export default {
  name: 'App',
  components: {
    Navbar, Page_Template
  }
}
</script>

<style>
#app {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>
