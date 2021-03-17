<template>
  <div id="app" :class="typeof weather != 'undefined' && weather.temperature > 80 ? 'warm' : ''">
    <div class="main">
      <div class="search-box">
        <input
        type="text"
        class="search-bar"
        placeholder="Search ..."
        v-model="query"
        @keyup.enter="fetchWeather"
        />
      </div>

      <div class="weather-wrapper" v-if="typeof weather != 'undefined'">
        <div class="location-box">
          <div class="location">{{ weather.location }} </div>
          <div class="date">{{ weather.date }} </div>
        </div>

        <div class="weather-box" v-if="typeof weather.temperature != 'undefined'">
          <div class="temp">{{ Math.round(weather.temperature) }} </div>
          <div class="weather">{{ weather.weather }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      api_key: "",
      url_base: "https://api.openweathermap.org/data/2.5",
      query: '',
      weather: {}
    }
  },
  methods: {
    fetchWeather() {
      if(this.query === "Puerto Rico") {
        this.setResults({
          location: "San Juan, PR, USA",
          date: "Tuesday 16 March 2021",
          temperature: "84",
          weather: "Hot"
        })
      } else {
        this.setResults({
          location: "Silver Spring, MD, USA",
          date: "Tuesday 16 March 2021",
          temperature: "55",
          weather: "Cool"
        })
      }

    },
    setResults(results) {
      this.weather = results
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
  color: rgb(20, 19, 19);
  opacity: 1; /* Firefox */
}

body {
  font-family: "montserrat", sans-serif;
}

#app {
  background: url("./assets/cold-bg.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

#app.warm {
  background: url("./assets/warm-bg.jpg");
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

.main {
  min-height: 100vh;
  padding: 20px;
}

.search-box {
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;
  color: #313131;
  font-size: 20px;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0px 16px 0px 16px;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.75);
  border-radius: 16px 0px 16px 0px;
}

.location-box .location {
  color: #FFF;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.location-box .date {
  color: #FFF;
  font-size: 20px;
  font-weight: 300;
  text-align: center;
  font-style: italic;
}

.weather-box {
  text-align: center;
}

.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #fff;

  font-size: 100px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 15px;
  margin: 30px 0px;

  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.weather-box .weather {
  color: #fff;
  font-size: 40px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
</style>
