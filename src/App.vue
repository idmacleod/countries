<template>
  <div id="app">
    <h1>Countries</h1>
  </div>
</template>

<script>
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
  }
}
</script>

<style>

</style>
