<template>
  <div id="app">
    <Header />
    <Hero />
    <Secondsection/>
    <Reach/>
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import Secondsection from './components/Secondsection.vue'
import Reach from './components/Reach.vue'

export default {
  name: 'App',
  components: {
    Header,
    Hero,
    Secondsection,
    Reach
  }
}
</script>

<style>
/* Global styles */
html, body, #app {
  width: 100%;
  min-height: 100vh;
  margin: 0;
  padding: 0;
  font-family: 'Poppins', sans-serif;
  background-color: #000000;
  color: #fff;
  box-sizing: border-box;
}

#app {
  width: 100%;
  min-height: 100vh;
  overflow-x: hidden;
  position: relative;
}
</style>
