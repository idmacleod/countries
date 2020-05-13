<template>
  <div id="app">
    <h1>Countries</h1>
    <countries-list :countries="countries"></countries-list>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList';

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
  },
  components: {
    'countries-list': CountriesList
  }
}
</script>

<style>

</style>
