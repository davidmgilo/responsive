<template>
  <div class="weather">
    <div class="location">{{location}}</div>
    <div class="date">{{date}}</div>
    <div class="description">{{description}}</div>
    <div class="current">
      <div class="visual">
        <div class="icon cloudy" alt="cloudy"></div>
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
        <div v-bind:class="'icon ' + forecast.icon"></div>
        <div class="forecast-temperature">
          <div class="high-temp">{{forecast.hightemp}}º</div>
          <div class="low-temp">{{forecast.lowtemp}}º</div>
        </div>
      </div>
    </div>
    <md-snackbar md-position="bottom center" ref="connectionError" md-duration="4000">
      <span>Connection error. Ensure the database is open. Loading default data.</span>
    </md-snackbar>
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
      forecasts: []
    }
  },
  methods: {
    fetchWeather: function () {
      this.$http.get('https://davidmgilo.github.io/responsive/static/weather.json').then((response) => {
        console.log(response.data)
        this.connecting = false
        this.forecasts = response.data
      }, (response) => {
        console.log(response.data)
        this.connecting = false
        this.loadDefaultData()
        this.showConnectionError()
        this.authorized = false
      })
    },
    showConnectionError: function () {
      this.$refs.connectionError.open()
    },
    loadDefaultData: function () {
      this.forecasts = [
          {'date': 'Monday', 'icon': 'rainy', 'hightemp': 45, 'lowtemp': 28},
          {'date': 'Tuesday', 'icon': 'stormy', 'hightemp': 45, 'lowtemp': 28},
          {'date': 'Wednesday', 'icon': 'rainy', 'hightemp': 45, 'lowtemp': 28},
          {'date': 'Thursday', 'icon': 'partcloudy', 'hightemp': 45, 'lowtemp': 28},
          {'date': 'Friday', 'icon': 'rainy', 'hightemp': 45, 'lowtemp': 28},
          {'date': 'Saturday', 'icon': 'stormy', 'hightemp': 45, 'lowtemp': 28},
          {'date': 'Sunday', 'icon': 'sunny', 'hightemp': 45, 'lowtemp': 28}
      ]
    }
  },
  created: function () {
    this.fetchWeather()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.weather{
  width: 100%;
  padding: 20px;
  box-shadow: 0 100px 100px rgba(0,0,0,0.2);
}

@media (min-width:700px){
  .weather {
    width: 700px;
  }
}

.location {
  font-size: 3em;
  color: black;
}

.date {
  font-size: 1.5em;
}

.description {
  font-size: 1.1em;
}

.current {
  overflow:auto;
  width: 100%;
}

.visual {
  float: left;
  width: 50%;
}

.text {
  float: right;
  width: 50%;
}

.forecast-day{
  display: inline-block;
  width: 14.285%;
}

.visual .icon {
  width:64px;
  height: 64px;
}

.forecast-day .icon {
  width: 64px;
  height: 64px;
}

.forecast-day .date {
  color: black;
  font-size: 0.7em;
  text-align: center;
  font-weight: bold;
}

.icon {
  background-repeat: no-repeat;
  background-size: contain;
  margin-left: auto;
  margin-right: auto;
}

.icon.cloudy {
  background-image: url("../assets/cloudy.png");
}

.icon.sunny {
  background-image: url("../assets/sunny.png");
}

.icon.stormy {
  background-image: url("../assets/thunderstorms.png");
}

.icon.partcloudy {
  background-image: url("../assets/partly_cloudy.png");
}

.icon.rainy {
  background-image: url("../assets/rain_s_cloudy.png");
}

.icon.rain {
  background-image: url("../assets/rain.png");
}

.visual .temp, .visual .scale, .visual .icon{
  display: inline-block;
}

.visual .temp{
  font-size: 1.6em;
}

.visual .scale, .visual .temp {
  vertical-align: top;
}

.forecast-day .high-temp, .forecast-day .low-temp {
  display: inline-block;
}

.forecast-day .low-temp{
  color: rgba(0,0,0,0.4);
}

.forecast-day .forecast-temperature {
  text-align: center;
}


@media (max-width: 650px){
  .location{
    font-size: 5em;
  }

  .forecast-day {
    display: block;
    border-top: 1px solid black;
    width:100%;
  }
  .forecast-day .date {
    width: 50%;
    text-align: left;
  }

  .date, .icon, .high-temp, .low-temp {
    display: inline-block;
  }
}

</style>
