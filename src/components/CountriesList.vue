<template>
    <select v-on:change="handleSelect" v-model.number="selectedIndex">
        <option value="" disabled>-- Select Country --</option>
        <list-component v-for="(country, index) in countries"
            :key="index"
            :value="index"
            :country="country"
        ></list-component>
    </select>
</template>

<script>
import { eventBus } from '../main.js';
import ListComponent from './ListComponent.vue';

export default {
    data: function () {
        return {
            selectedIndex: ""
        }
    },
    name: 'countries-list',
    props: ['countries'],
    components: {
        'list-component': ListComponent
    },
    methods: {
        handleSelect: function () {
            eventBus.$emit('country-selected', this.countries[this.selectedIndex]);
        }
    }
};
</script>

<style>

</style>