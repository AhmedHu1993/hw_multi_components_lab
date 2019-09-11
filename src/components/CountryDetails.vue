<template>
  <article v-if="country">
    <p>{{ country.name }}</p>
    <p>{{ country.capital }}</p>
    <p>{{ country.population }}</p>
  </article>
</template>

<script>
export default {
  name: 'country-details',
  props: ['country']
};
</script>

<style>
</style>
