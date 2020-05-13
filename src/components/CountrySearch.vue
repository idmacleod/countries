<template>
    <div>
        <h2>...or search by name:</h2>
        <input type="search" name="search" id="search" v-model="searchInput">
    </div>
</template>

<script>
export default {
    name: 'country-search',
    data: function () {
        return {
            searchInput: ""
        }
    }
}
</script>

<style>

</style>