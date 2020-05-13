<template>
  <div id="app">
    <header>
      <h1>Vue Countries</h1>
      <countries-list :countries="countries"></countries-list>
      <country-search></country-search>
    </header>
    <div v-if="searchResult">
      <p>Your search matched {{searchResult.length}} countries:</p>
      <ul>
        <list-component v-for="(country, index) in searchResult" :key="index" :country="country"></list-component>
      </ul>
    </div>
    <country-detail :country="selectedCountry"></country-detail>
  </div>
</template>

<script>
import { eventBus } from './main.js';
import CountriesList from './components/CountriesList.vue';
import CountrySearch from './components/CountrySearch.vue';
import ListComponent from './components/ListComponent.vue';
import CountryDetail from './components/CountryDetail.vue';

export default {
  name: 'app',
  data: function () {
    return {
      countries: [],
      selectedCountry: null,
      searchResult: null
    }
  },
  mounted: function () {
    fetch('https://restcountries.eu/rest/v2/all')
      .then(res => res.json())
      .then(countries => this.countries = countries)
      .catch(error => console.log(error));

    eventBus.$on('country-selected', (country) => {
      this.searchResult = null;
      this.selectedCountry = country;
    });

    eventBus.$on('search-complete', (result) => {
      this.selectedCountry = null;
      if (result.length == 1) {
        this.selectedCountry = result[0];
        this.searchResult = null;
      } else {
        this.searchResult = result;
      }
    });
  },
  components: {
    'countries-list': CountriesList,
    'country-search': CountrySearch,
    'list-component': ListComponent,
    'country-detail': CountryDetail
  }
};
</script>

<style>
  #app {
    font-family: 'Courier New', Courier, monospace;
  }
  header {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
  }
</style>
