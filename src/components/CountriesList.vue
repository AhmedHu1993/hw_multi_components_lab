<template>
  <ul>
    <list-item v-for="(country, index) in mappedCountries" :key="index" :country="country"></list-item>
  </ul>
</template>

<script>
import ListItem from './ListItem.vue';
export default {
  name: 'countries-list',
  props: ['mappedCountries'],
  components: {
    'list-item': ListItem
  }
};
</script>

<style>
</style>
