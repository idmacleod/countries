<template>
    <li v-on:click="handleClick">{{ country.name }}</li>
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'list-component',
    props: ['country'],
    methods: {
        handleClick: function () {
            eventBus.$emit('country-selected', this.country);
        }
    }
};
</script>

<style>
    li {
        cursor: pointer;
    }
</style>