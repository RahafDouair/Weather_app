
<template>
  <main>
<div class="section">
  <h2 class="text-center mb-4 title">
  Weather App
  </h2>
  <div class="container">
    <input class="form-control" v-model="query" @keypress="fetchWeather" type="search" id="search" placeholder="Search City">
<div class="weather-wrapper">
<div class="location" v-if="typeof weather.main!='undefined'">
<div class="loaction-name mt-4 text-center">
<h2 class="text-center">{{ weather.name }}{{ weather.sys.country }}</h2>
<p>{{ new Date() }} </p>
</div>
<div class="degree text-center">
<h4>{{ Math.round(weather.main.temp) }} <strong> ْ</strong> C</h4>
<p>{{ weather.weather[0].main }}</p>
</div>
</div>
</div>
  </div>
</div>

  </main>
</template>
<script>
export default {
 data:()=>({
  api_key:'c5c94a57716d0ea2b9fb924b3b9f6b9b',
url_api:'https://api.openweathermap.org/data/2.5/',
query:'',
weather:{},
results:[]
}),
created(){

},
methods:{
 
  fetchWeather(e){
  // const api_url = `${this.url_api}weather?q=${this.query}&units=metric&
  if(e.key=="Enter")
{
  fetch(`${this.url_api}weather?q=${this.query}&units=metric&appid=${this.api_key}`)
  .then( res=>{
    return res.json();
  }).then(this.setResults);
} 

},
setResults(results){
  this.weather = results;
}


}


}
</script>
<style scoped>
.title{
  font-family: "Edu TAS Beginner", cursive;
  font-optical-sizing: auto;
  font-weight: 500;
  font-style: normal;
  color:white
}
.section{
  font-family: "Edu TAS Beginner", cursive;
  font-optical-sizing: auto;
  font-weight: 500;
  background-image:url('../assets/weather.jpg');
  height: 100vh;
  background-size: cover;
  background-repeat: no-repeat;
background-image:linear-gradient(to bottom ,rgba(0 ,0,0,0.25) ,rgba(0 ,0,0,0.75));
}
.degree{
  font-family: "Edu TAS Beginner", cursive;
  font-optical-sizing: auto;
  font-weight: 500;
  background: #4b4b4b;
    color: white;
    width: 36%;
    transform: translate(91%);
    padding: 24px;
    font-size: 25px;
    border-radius: 29px;
  }
.degree h4 {
  font-size: 49px;

  }


</style>