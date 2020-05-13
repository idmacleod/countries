<template>
    <div v-if="country">
        <li v-on:click="handleClick">{{ country.name }}</li>
    </div>
  
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'list-component',
    props: ['country'],
    methods: {
        handleClick: function () {
            eventBus.$emit('country-clicked', this.country);
        }
    }
}
</script>

<style>

</style>