<template>
  <ul>
    <li v-for="(ciudad, i) in citiesFromApp" :key="i">
      <h4>{{ ciudad.name }}</h4>
      <img :alt="ciudad.name" :src="ciudad.image" width="400"/>
      <p>{{ ciudad.about }}</p>
    </li>
  </ul>
</template>

<script>
export default {
  name: "CitiesList",
  props: ["citiesFromApp"],
  data() {
    return {};
  },
};
</script>

<style>
ul {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
    list-style: none;
}
</style>
