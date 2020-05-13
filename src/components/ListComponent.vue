<template>
    <div v-if="country">
        <li>{{ country.name }}</li>
    </div>
  
</template>

<script>
export default {
    name: 'list-component',
    props: ['country']
}
</script>

<style>

</style>