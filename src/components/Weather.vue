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
    <div class="forecast">
      <div class="forecast-day" v-for="forecast in forecasts">
        <div class="date">{{forecast.date}}</div>
        <div class="icon">{{forecast.icon}}</div>
        <div class="high-temp">{{forecast.hightemp}}</div>
        <div class="low-temp">{{forecast.lowtemp}}</div>
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
      pollen: 36,
      forecasts: [
        {'date': 'Monday', 'icon': 'cloud', 'hightemp': 45, 'lowtemp': 28},
        {'date': 'Tuesday', 'icon': 'sunny', 'hightemp': 45, 'lowtemp': 28},
        {'date': 'Wednesday', 'icon': 'cloudy', 'hightemp': 45, 'lowtemp': 28},
        {'date': 'Thursday', 'icon': 'rainy', 'hightemp': 45, 'lowtemp': 28},
        {'date': 'Friday', 'icon': 'rainy', 'hightemp': 45, 'lowtemp': 28},
        {'date': 'Saturday', 'icon': 'rainy', 'hightemp': 45, 'lowtemp': 28},
        {'date': 'Sunday', 'icon': 'rainy', 'hightemp': 45, 'lowtemp': 28}
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>



</style>
