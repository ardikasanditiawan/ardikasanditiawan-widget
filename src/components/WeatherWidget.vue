<template>
  <div class="weather-widget">
    <h2 class="widget-title">Cuaca</h2>
    <div class="location-input">
      <label class="butt" for="location">Masukan Lokasimu :</label>
      <input type="text" id="location" v-model="location" />
      <button @click="fetchWeatherData" class="button-primary">Lihat</button>
    </div>
    <div v-if="weatherData" class="weather-data">
      <div class="data-box">
        <p class="location">Location: {{ weatherData.name }}</p>
      </div>
      <div class="data-box">
        <p v-if="weatherData.main" class="temperature">
          Temperature: {{ weatherData.main.temp }}°C
        </p>
      </div>
      <div class="data-box">
        <p v-if="weatherData.weather" class="description">
          Description: {{ weatherData.weather[0].description }}
        </p>
      </div>
    </div>
    <p class="tuu" v-else>Mencari Data Cuaca...</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      location: '',
      weatherData: null
    };
  },
  methods: {
    async fetchWeatherData() {
      try {
        const apiKey = 'b7bfca7b27a3485144fea086c50d09dc';
        const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${this.location}&appid=${apiKey}`;

        const response = await fetch(apiUrl);
        const data = await response.json();

        this.weatherData = data;
      } catch (error) {
        console.error('Error fetching weather data:', error);
      }
    }
  }
};
</script>

<style scoped>
.widget-title{
  display:inline-block;
  background-color: rgba(49, 49, 49, 0.1);
  padding: 10px 9px;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  color: rgb(252, 252, 252);
}
.widget-title {
  margin: 4px 3px 12px;
  color: rgb(197, 231, 0);
}


.tuu {
  display:inline-block;
  background-color: rgba(21, 255, 0, 0.1);
  padding: 10px 9px;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  color: rgb(0, 0, 0);

  
}

.tuu {
  margin: 4px 3px 12px;
  color: rgb(197, 231, 0);
}


.butt {
  display:inline-block;
  background-color: rgba(21, 255, 0, 0.1);
  padding: 10px 9px;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  color: rgb(0, 0, 0);
  
}

.butt {
  margin: 4px 3px 12px;
  color: rgb(197, 231, 0);
  
}


.weather-widget {
  border: 1px solid #ccc;
  padding: 20px;
  margin-bottom: 20px;
  text-align: center;
  background-color: #929292;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.widget-title {
  margin-top: 0;
  
  font-size: 24px;
}

.location-input {
  margin-bottom: 10px;
}

.location-input label {
  color: #fff;
  font-size: 16px;
}

.location-input input {
  width: 200px;
  padding: 10px;
  margin-left:12px;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  background-color: #f5f5f5;
  color: #333;
}

.button-primary {
  padding: 10px 20px;
  margin: 21px;
  background-color: #4caf50;
  color: rgb(255, 255, 255);
  border: none;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.button-primary:hover {
  background-color: #45a049;
}

.weather-data {
  margin-top: 10px;
  color: #000000;
}

.data-box {
  background-color: rgba(255, 255, 255, 0.1);
  padding: 10px;
 border-radius: 4px;
  margin-bottom: 10px;
}

.location {
  font-size: 18px;
  font-weight: bold;
}

.temperature {
  font-size: 24px;
  color: #000000;
}

.description {
  font-size: 16px;
}
</style>
