<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}

/* fetch('https://restcountries.eu/rest/v2/region/europe')
.then(res => res.json())
.then(data => {
  data.forEach(country => {
    console.log(country.name)
  });
})
.catch(error => {
  console.log(`Error: \n\n ${error.name}`)
  }) */

//async await
const getCountries = async() => {
  try{
    const result = await fetch('https://restcountries.eu/rest/v2/region/europe')
    const data = await result.json()
    /* data.forEach(country => {
      console.log(country.name)
    }); */
    // const arrayCountriesNames = data.map(country => country.name)
    //Countries population bigger than 20 million people
    const arrayCountriesFiltered = data.filter(country => country.population > 20000000)
    console.log(arrayCountriesFiltered)
  }catch(error) {
    console.log(error)
  }
}

getCountries()
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
