<template>
  <Nav />
  <div id='header'>
    <h1>Express News</h1>
  </div>
  <Home />
</template>

<script>
import Home from './components/Home.vue'
import Nav from './components/Navbar.vue'

export default {
  name: 'App',
  components: {
    Nav,
    Home
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
}
#header{
  font-family: 'Times New Roman', Times, serif;
}
</style>
