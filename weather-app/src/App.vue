<template>
  <div id="app">
    <h1>Weather App</h1>
    <input v-model="city" type="text" placeholder="Enter a city" />
    <button @click="fetchWeather">Search</button>
    
    <div v-if="weatherData">
      <h2>{{ weatherData.location.name }}</h2>
      <h3>{{ weatherData.current.temp_c }}°C</h3>
      <p>{{ weatherData.current.condition.text }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      city: '',
      weatherData: null,
    };
  },
  methods: {
    async fetchWeather() {
      const response = await axios.get(
        `http://api.weatherapi.com/v1/current.json?key=d1292c3ac84742c395600552231607&q=${this.city}`
      );
      this.weatherData = response.data;
    },
  },
};
</script>

<style>
#app {
  text-align: center;
  margin-top: 60px;
}
</style>
