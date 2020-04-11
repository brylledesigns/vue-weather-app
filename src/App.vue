<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input 
          class="search-bar" 
          type="text"
          placeholder="Search a place..."
          v-model="query"
          @keypress="fetchWeather"
        />
      </div>

      <div class="content" v-if="typeof weather.main != 'undefined'">
        <div class="location-box">
          <div class="location">
            {{ weather.name }}, {{weather.sys.country}}
          </div>
          <div class="date">
            March 11 2020
          </div>
        </div>

        <div class="weather-container">
          <div class="temp">25°c</div>
          <div class="weather">Sunny</div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      api_key: '03fd3c24b91fc1a3c93a991e8d5e1543',
      url_base: "api.openweathermap.org/data/2.5/",
      query: '',
      weather: {}
    }
  },
  methods: {
    fetchWeather(e) {
      if(e.key == "Enter") {
        fetch(`${this.url_base}weather?q=${this.query}&appid=${this.api_key}`)
        .then(res=> {
          return res.json();
        }).then(this.setResults);
      }
    },

    setResults (results) {
      this.weather = results;
    }
  }
}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  #app {
    background-image: url('./assets/hot.jpg');
    background-size: cover;
    background-position: bottom;
    transition: 0.5s;
  }

  main {
    height: 100vh;
    background-size: cover;
    background-position: bottom;
    background-image:linear-gradient(to bottom, rgba(0, 0, 0, 0.151), rgba(0, 0, 0, 0.377));
    display: flex;
    flex-direction: column;
    flex-wrap: nowrap;
    align-items: center;
  }

  .search-box {
    /* margin-left: 290px; */
    margin-top: 50px;
    float: left;
  }

  .search-box .search-bar {
    width: 500px;
    height: 80px;
    font-size: 30px;
    font-weight: bold;
    background: transparent;
    color: white;
    text-align: center;
    border: none;
    cursor: pointer;
  }

  .search-bar:focus {
    outline: none;
    border: 1px solid white;
    border-top: none;
    border-right: none;
    border-left: none;
  }

  ::placeholder {
    color: white;
  }

  .content {
    margin-top: 50px;
    color: white;
    text-align: center;
  }

  .location-box .location {
    font-weight: bold;
    font-size: 25px;
  }

  .location-box .date {
    font-size: 18px;
    margin-top: 10px;
  }

  .weather-container {
    margin-top: 20px;
  }

  .weather-container .temp {
    font-size: 100px;
  }

  .weather-container .weather {
    font-size: 20px;
  }
</style>
