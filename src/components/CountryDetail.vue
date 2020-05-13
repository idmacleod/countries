<template>
    <div v-if="country">
        <h3>{{ country.name }}</h3>
        <ul>
            <li>Capital: {{country.capital}}</li>
            <li>Population: {{country.population}}</li>
            <li>Languages Spoken:
            <ul>
                <li v-for="(language, index) in country.languages" :key="index">{{language.name}}</li>
            </ul>
            </li>
        </ul>
        <img :src="country.flag" alt="flag">
    </div>
</template>

<script>
export default {
    name: 'country-detail',
    props: ['country']
};
</script>

<style>

</style>