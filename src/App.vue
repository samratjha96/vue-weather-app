<template>
  <div id="app">
    <div class="main">
      <div class="search-box">
        <input type="text" class="search-bar" placeholder="Search ..."/>
      </div>

      <div class="weather-wrapper">
        <div class="location-box">
          <div class="location">Silver Spring, MD, USA</div>
          <div class="date">Tuesday 16 March</div>
        </div>

        <div class="weather-box">
          <div class="temp">55 degrees</div>
          <div class="weather">Cold</div>
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
      api_key: "testApiKey"
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
</style>
