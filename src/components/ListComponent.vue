<template>
    <li class="clickable" v-on:click="handleClick">{{ country.name }}</li>
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
    .clickable {
        cursor: pointer;
    }

    .clickable:hover, .clickable:active {
        text-decoration: underline;
    }
</style>