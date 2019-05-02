<template>
  <div id="app">
    <h1>Countries List</h1>
    <countries-list :countries="countries"></countries-list>
    <country-detail :country="selectedCountry"></country-detail>

  </div>
</template>

<script>
import CountryDetail from './components/CountryDetail.vue';

import CountryList from './components/CountriesList.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries);

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    });
  },
  components: {
    "countries-list": CountryList,
    "country-detail": CountryDetail
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
