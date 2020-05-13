<template>
    <div>
        <select v-on:change="handleSelect" v-model.number="selectedIndex">
            <option value="" disabled>Select a country...</option>
            <option v-for="(country, index) in countries" :key="index" :value="index">
                {{ country.name }}
            </option>
        </select>
    </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    data: function () {
        return {
            selectedIndex: ""
        }
    },
    name: 'countries-list',
    props: ['countries'],
    methods: {
        handleSelect: function () {
            eventBus.$emit('country-selected', this.countries[this.selectedIndex]);
        }
    }
};
</script>

<style>

</style>