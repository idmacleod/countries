<template>
    <select>
        <list-component v-for="(country, index) in countries" :key="index" :country="country"></list-component>
    </select>
</template>

<script>
import ListComponent from './ListComponent';

export default {
    name: 'countries-list',
    props: ['countries'],
    components: {
        'list-component': ListComponent
    }
};
</script>

<style>

</style>