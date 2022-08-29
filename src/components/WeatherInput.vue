<template>
  <div class="search-box">
    <input id="input-city" type="text" class="search-bar" placeholder="Search a city" v-model="query"
          @keypress.enter="addCity">
    <button id="add-city" v-on:click="addCity">+</button>  
  </div>
</template>

<script>


export default {
  data() {
      return {
        api_key: '72e1943fa5a68f4a887bbfef71dc7b1a',
        url_base: 'https://api.openweathermap.org/data/2.5/',
        query: '',
        weather: {}
      }
  },
  components: {

  },
  methods: {
    addCity() {
      /* this.cities.push({id: this.cities.length+1, label: this.query}) */
      this.fetchWeather()
      this.query= ''
    },
    deleteCity() {
      
    },    
    async fetchWeather () {
        const res = await fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`) 
        const result = await res.json()
        this.setResults(result)
      
    },
    setResults (results) {
      //this.cities.push(results) 
      this.$emit('results_emit', results)
    }
  }
}

</script>

<style>

.search-box {
  width: 100%;
  padding: 12px;
}

.search-box .search-bar {
  display: inline-block;
  width: 90%;
  color: rgb(13, 9, 9);
  font-size: 20px;
  padding: 12px;
  border: none;
  outline: none;
  background: none;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.6);
  border-radius: 0px 0px 0px 20px;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.75);
  background-color: rgba(255, 255, 255, 1);
  border-radius: 20px 0px 0px 0px;
}

button {
  background-color: rgba(255, 255, 255, 0.6);
  box-shadow: 4px 0px 4px rgba(0, 0, 0, 0.25);
  border: none;
  height: 47px;
  padding-bottom: 1.5px;
  font-size: 24px;
  font-weight: bold;
  width: 10%;
  color: rgb(255, 0, 128);
}

button:active {
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.75);
  background-color: rgba(255, 255, 255, 1);
  transition: 0.1;
}
</style>