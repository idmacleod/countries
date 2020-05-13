<template>
  <div id="app">
    <h1>Countries</h1>
    <countries-list :countries="countries"></countries-list>
    <country-search></country-search>
    <country-detail :country="selectedCountry"></country-detail>
  </div>
</template>

<script>
import { eventBus } from './main.js';
import CountriesList from './components/CountriesList.vue';
import CountrySearch from './components/CountrySearch.vue';
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
      .then(countries => this.countries = countries)
      .catch(error => console.log(error));

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    });
  },
  components: {
    'countries-list': CountriesList,
    'country-search': CountrySearch,
    'country-detail': CountryDetail
  }
};
</script>

<style>

</style>
