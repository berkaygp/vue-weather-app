<!-- **yapılacaklar** -->
<!-- deleteCity i çalışır hale getir(filter, id...) -->
<!-- şehir isimlerinin yanındaki province ları sil(arraya ekleyip) --> 
<!-- iconların width, padding ayarla -->


<template>
  <div id="app">
    <header>
      <h1>#OnlyCentigrade</h1>
    </header>
    <WeatherInput @results_emit="addToCities" />
    <div class="date-box">
        <div class="date">{{ dateBuilder() }}</div>
    </div>
    <WeatherCityList :city_list="cities" @deleteCity="deleteCity" />
  </div>
  
</template>

<script>
import WeatherInput from './components/WeatherInput.vue';
import WeatherCityList from './components/WeatherCityList.vue';

export default {
  name: 'App',
  data() {
    return {
      cities: []
    }
  },
  components: {
    "WeatherInput": WeatherInput,
    "WeatherCityList": WeatherCityList,
  },
  methods: {
    addToCities(results) {
      this.cities.push(results)
    },
    deleteCity() {

    },
    dateBuilder() {
      let d = new Date;
      let months =  ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();

      return `${day}, ${date} ${month} ${year}`;
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto+Mono:ital@1&family=Roboto:wght@700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@900&display=swap');


* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Roboto', sans-serif;
}

#app {
  background: linear-gradient(35deg, rgb(107, 40, 216) 60%, rgb(10, 211, 211));
  transition: 0.4s;
  min-height: 100vh;
}

h1 {
    text-align: start;
    font-family: 'Noto Sans JP', sans-serif;
    font-size: 36px;
    font-weight: 700;
    color: black;
    padding-left: 16px;
}

.date-box {
  padding-bottom: 60px;
  
}

.date-box .date {
  text-align: center;
  color: white;
  font-size: 36px;
  padding-left: 25px;
  font-weight: 600;
  
}
</style>
