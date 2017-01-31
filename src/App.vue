<template>
  <div id="app">
    <weather></weather>
  </div>
</template>

<script>
import Weather from './components/Weather'

export default {
  name: 'app',
  components: {
    Weather
  }
}
</script>

<style>

body{
  font-family: Roboto, Arial;
  font-size: 1.2em;
  color: #555;
}

</style>
