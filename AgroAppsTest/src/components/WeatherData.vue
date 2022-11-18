<script>

export default {
  props: {
    weather: {
      type: Object,
      required: true
    }
  }
}

// defineProps({
//   weather: {
//     type: Object,
//     required: true
//   }
// })
</script>

<template>
  <div class="weatherInfo">
    <!-- <label>{{ weather.weather[0].icon }}</label> -->
    <!-- <label>{{ weather.weather[0].description }}</label> -->
    <img src="http://openweathermap.org/img/wn/10d@2x.png" />
    <!-- <img src="http://openweathermap.org/img/wn/+${weather.weather[0].icon}@2x.png" /> -->
    <h1 class="temperature">{{ weather.temp }} &deg;C</h1>
    <h3>Feels like {{ weather.feels_like }} &deg;C</h3>
    <div class="weatherDetails">
      <div class="details">
        <label>Pressure</label>
        <h3>{{ weather.pressure }}</h3>
      </div>
      <div class="details">
        <label>Humidity</label>
        <h3>{{ weather.humidity }}%</h3>
      </div>
      <div class="details">
        <label>Wind Speed</label>
        <h3>{{ weather.wind_speed }}</h3>
      </div>
      <div class="details">
        <label>Wind Degrees</label>
        <h3>{{ weather.wind_deg }}</h3>
      </div>
      <div class="details">
        <label>Clouds</label>
        <h3>{{ weather.clouds }}</h3>
      </div>
    </div>
  </div>
</template>

<style scoped>
h1,
h3,
label {
  color: navy;
}

.temperature {
  font-size: 5vw;
}

.weatherInfo {
  display: flex;
  flex-direction: column;
  justify-self: center;
  align-items: center;
}

.weatherDetails {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 2em;
}

.details {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 1em 1em;
  padding: 1em;
  background-color: rgba(240, 240, 240, 0.1);
  box-shadow: rgba(255, 255, 255, 0.76) 0px 22px 70px 4px;
  border-radius: 1rem;
  border: 2px solid navy;
}

.details h3 {
  font-weight: bold;
}

@media (max-width: 1024px) {
  .weatherInfo {
    margin-bottom: 2rem;
  }
}
</style>
