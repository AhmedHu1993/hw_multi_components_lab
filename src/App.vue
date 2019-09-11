<template>
  <div id="app">
    <country-details :country="selectedCountry"></country-details>
    <countries-list :mappedCountries="mappedCountries"></countries-list>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import CountryDetails from './components/CountryDetails.vue';
import { eventBus } from './main.js';

export default {
  name: 'app',
  data() {
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted() {
    fetch('https://restcountries.eu/rest/v2/all')
      .then(response => response.json())
      .then(data => (this.countries = data));

    eventBus.$on('country-selected', country => {
      this.selectedCountry = country;
    });
  },
  methods: {},
  computed: {
    mappedCountries() {
      return this.countries.reduce((map, country) => {
        map[country.alpha3Code] = country;
        return map;
      }, {});
    }
  },
  components: {
    'countries-list': CountriesList,
    'country-details': CountryDetails
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
