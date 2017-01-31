<template>
  <div class="weather">
    <div class="location">{{location}}</div>
    <div class="date">{{date}}</div>
    <div class="description">{{description}}</div>
    <div class="current">
      <div class="visual">
        <div class="cloud">cloud</div>
        <div class="temp">{{temp}}</div>
        <div class="scale">º</div>
      </div>
      <div class="text">
        <div class="precipitation">Precipitation: {{precipitation}}</div>
        <div class="humidity">Humidity: {{humidity}}</div>
        <div class="wind">Wind: {{wind}}</div>
        <div class="pollen">Pollen: {{pollen}}</div>
      </div>
    </div>
  </div>
  
</template>

<script>
export default {
  name: 'weather',
  data () {
    return {
      location: 'New York, NY',
      date: 'Tuesday, April 15th',
      description: 'desc here',
      temp: 25,
      precipitation: '100%',
      humidity: '97%',
      wind: '4mph SW',
      pollen: 36
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
