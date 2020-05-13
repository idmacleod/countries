<template>
    <div>
        <input type="search" name="search" id="search" v-model="searchInput" placeholder="Search for a country...">
        <button v-on:click="handleSearch">Search</button>
    </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'country-search',
    data: function () {
        return {
            searchInput: "",
        }
    },
    methods: {
        handleSearch: function () {
            fetch(`https://restcountries.eu/rest/v2/name/${this.searchInput}`)
                .then(res => res.json())
                .then(searchResults => eventBus.$emit('search-complete', searchResults))
                .catch(error => console.log(error));
        }
    }
};
</script>

<style>

</style>