<template>
  <div id="app">
    <div id='header'> 
      <NavBar />
      <PatientBlock />
    </div>
    <BodyBlock :search="search"/>
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import PatientBlock from './components/PatientBlock.vue'
import BodyBlock from './components/BodyBlock.vue'

export default {
  name: 'App',
  components: {
    NavBar,
    PatientBlock,
    BodyBlock,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-left: -8px;
  width: 1440px;
}

</style>
