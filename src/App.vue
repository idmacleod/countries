<template>
  <div id="app">
    <h1>Countries</h1>
    <country-detail :country="selectedCountry"></country-detail>
    <countries-list :countries="countries"></countries-list>
  </div>
</template>

<script>
import { eventBus } from './main.js';
import CountriesList from './components/CountriesList.vue';
import CountryDetail from './components/CountryDetail.vue';

export default {
  name: 'app',
  data: function () {
    return {
      countries: [],
      selectedCountry: null
    }
  },
  mounted: function () {
    fetch('https://restcountries.eu/rest/v2/all')
      .then(res => res.json())
      .then(countries => this.countries = countries);

    eventBus.$on('country-clicked', (country) => {
      this.selectedCountry = country;
    });
  },
  components: {
    'countries-list': CountriesList,
    'country-detail': CountryDetail
  }
};
</script>

<style>

</style>
