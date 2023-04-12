
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="date">{{ todaysDate() }}</div>
   <input type="text" placeholder="Search..." class="search-bar" 
v-model="query" v-on:keypress="fetchWeather" />
   </div>
</template>

<script>
import axios from "axios";
export default {
  name: 'WeatherApp',
  props: {
    msg: String
  },
  data() {
    return {
      api_key: "",
      url_base: "https://api.openweathermap.org/data/2.5/",
      weather_icon: "http://openweathermap.org/img/wn/",
      query: "",
      weather: {},
    };
},
  methods: {
    async fetchWeather(e) {
      if (e.key == "Enter") {
    let response = await axios.get(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`);
    this.setResults(response.data);
  }
},
  setResults(returnedResponse) {
    this.weather = returnedResponse;
  },
  todaysDate() {
    const months = ["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec",];
    const days = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];
    let d = new Date();
    let month = months[d.getMonth()];
    let day = days[d.getDay()];
    let date = d.getDate();
    let year = d.getFullYear();
  return `Date: ${month} ${date} ${day} ${year}`;
}
},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
