<template>
   <Weather msg="Welcome to Vue Weather App"/>
</template>

<script>
import Weather from './components/weather.vue'

export default {
  name: 'App',
  components: {
    Weather
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
