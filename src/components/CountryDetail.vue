<template>
    <div id="details" v-if="country">
        <img :src="country.flag" alt="flag">
        <div id="facts">
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
        </div>
    </div>
</template>

<script>
export default {
    name: 'country-detail',
    props: ['country']
};
</script>

<style>
    #details {
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        margin: 0;
    }

    img {
        width: 50%;
    }

    #facts {
        font-size: 150%;
    }
</style>