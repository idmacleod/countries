<template>

    <div v-if="country">
        <h3>{{ country.name }}</h3>
    </div>
  
</template>

<script>
export default {
    name: 'country-detail',
    props: ['country']
}
</script>

<style>

</style>