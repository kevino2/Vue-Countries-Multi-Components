<template lang="html">
  <div>
    <ul>
      <list-item v-for="(country , index) in countries" :country="country" :key="index"></list-item>
    </ul>

    <select id="selectCountry" v-on:change="country-selected" v-model="selectedCountry">
      <option value="">Select Country</option>
      <option v-for="(country, index) in countries" :country="country">{{ country.name }}</option>
   </select>
  </div>

</template>
<script>



import ListItem from './ListItem.vue';

export default {
  name: 'countries-list',
  props: ['countries'],
  components: {
    "list-item": ListItem
  },
}
</script>

<style lang="css" scoped>
</style>
