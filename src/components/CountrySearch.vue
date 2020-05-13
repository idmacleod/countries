<template>
    <div>
        <h2>...or search by name:</h2>
        <input type="search" name="search" id="search" v-model="searchInput">
        <button v-on:click="handleSearch">Search</button>
        <p v-if="searchFailed">No Results</p>
        <ul v-if="searchResults">
            <list-component v-for="(country, index) in searchResults" :key="index" :country="country"></list-component>
        </ul>
    </div>
</template>

<script>
import ListComponent from './ListComponent.vue';

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
                .then(searchResults => {
                    this.searchResults = searchResults;
                    this.searchFailed = false;
                })
                .catch(this.searchFailed = true);
        }
    },
    components: {
        'list-component': ListComponent
    }
}
</script>

<style>

</style>