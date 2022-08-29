<template>
    <div class="wrap">
        <div class="weather-box" v-for="city in city_list" :key="city.id">
            <div class="location">
                {{ city.name }} 
                <i class="pi pi-times-circle" @click="deleteCity(city, city.id)"></i>
            </div>
            <div class="temp">{{ Math.round(city.main.temp) }}°c</div>
            <div class="weather">{{ city.weather[0].main }}</div>
            <div class="gif">
                 <div v-if="city.weather[0].main === 'Clouds'">
                    <img class="cloudIcon" :src="'https://i.gifer.com/origin/0d/0d6cf5b4980702758a616a14bed86e3a_w200.gif'" width="125"/>
                </div>
                <div v-else-if="city.weather[0].main === 'Clear'">
                    <img class="sunIcon" :src="'https://i.pinimg.com/originals/90/85/bb/9085bb2580eee46db433164fdcca9500.gif'"  width="150"/>
                </div>
                <div v-else-if="city.weather[0].main === 'Thunderstorm'">
                    <img class="thunderstormIcon" :src="'https://i.giphy.com/media/ln1W55MmaidLSj7wA5/giphy.webp'" width="200"/>
                </div>
                <div v-else-if="city.weather[0].main === 'Mist'">
                    <img class="mistIcon" :src="'https://icon-library.com/images/fog-icon-png/fog-icon-png-5.jpg'" width="130" />
                </div>
                <div v-else-if="city.weather[0].main === 'Snow'">
                    <img class="snowIcon" :src="'https://thumbs.gfycat.com/WellmadeSameBeaver-max-1mb.gif '"  width="120"/>
                </div>              
                <div v-else-if="city.weather[0].main === 'Rain'">
                    <img class="rainIcon" :src="'https://monophy.com/media/Su0pXI7m9Q8TvQuf8s/monophy.gif'" width="167"/>
                </div>              
            </div>
       </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            weather: '',
        }
    },
    props: ['city_list'],
    methods: {
        deleteCity(city, id){
            console.log('method is working');
            console.log(city);
            console.log(city.id);
        }
    }
}
</script>

<style>
.weather-box {
  background: rgba(255, 255, 255, 0.75);
  border-radius: 20px;
  margin: 20px;
  text-align: center;
  padding: 30px 10px;
  max-width: 500px;
  min-width: 400px;
}

.weather-box .temp {
  color: black;
  font-size: 110px;
  font-weight: 600;
}

.weather-box .weather {
  color: black;
  font-size: 24px;
  font-weight: 600;
  font-style: italic;
}

.weather-box .location {
  color: black;
  font-size: 48px;
  padding-left: 25px;
  font-weight: 600;
}

i {
    color: red;
    /*padding-left: 40px;*/
    margin-left: 2rem;
    cursor: pointer;
    
}

.location {
    margin-left: 50px;
}

.wrap {
    display: flex;
    justify-content: center;
}

.cloudIcon {
    padding-top: 35px;
}

.sunIcon {
    padding-top: 10px;
}

.thunderstormIcon {
    padding-top: 8px;
}

/* .mistIcon {

}

.snowIcon {

}
.rainIcon {

} */
</style>