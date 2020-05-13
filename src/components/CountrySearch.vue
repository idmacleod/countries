<template>
    <div>
        <h2>...or search by name:</h2>
        <input type="search" name="search" id="search" v-model="searchInput">
        <button v-on:click="handleSearch">Search</button>
    </div>
</template>

<script>
export default {
    name: 'country-search',
    data: function () {
        return {
            searchInput: "",
            searchFailed: false,
            searchResults: []
        }
    },
    methods: {
        handleSearch: function () {
            fetch(`https://restcountries.eu/rest/v2/name/${this.searchInput}`)
                .then(res => res.json())
                .then(searchResults => this.searchResults = searchResults)
                .catch(this.searchFailed = true);
        }
    }
}
</script>

<style>

</style>