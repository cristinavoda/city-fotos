<template>
  <!-- HTML -->
  <h1>{{ welcomeSentence }}</h1>
  <img
    id="cover-image"
    alt="my city image"
    :src="cities[cities.length - 1].image"
    width="600"
  />
  <button @click="showForm = true" :class="{ choosen: showForm }">
    New city
  </button>
  <button @click="showForm = false" :class="{ choosen: !showForm }">
    My cities
  </button>
  <Form v-if="showForm" @sendCitytoApp="addCity" />
  <CitiesList v-else :citiesFromApp="cities" />
</template>

<script>
// JavaScript

/**--- Import zone: ----*/
import CitiesList from "./components/CitiesList.vue";
import Form from "./components/Form.vue";
/**--- Import zone: ----*/

export default {
  name: "App",
  components: { CitiesList, Form },
  data() {
    return {
      cities: [
        {
          name: "Barcelona",
          about:
            "Barcelona, la capital cosmopolita de la región de Cataluña en España, es conocida por su arte y arquitectura. ",
          image: "/images/barcelona.jpeg",
        },
      ],
      showForm: true,
      character: "",
      planet: "",
      charNum: "",
    };
  },
  methods: {
    addCity(cityfromForm) {
      this.cities.push(cityfromForm);
      console.log(this.cities);
      return this.cities;
    },

  },
  computed: {
    welcomeSentence() {
      return `My city is: ${this.cities[this.cities.length - 1].name}`;
    },
  },
};
</script>

<style>
/* CSS */
.choosen {
  background-color: rgb(29, 217, 192);
  color: rgb(42, 42, 42);
  font-weight: bold;
}

#cover-image {
  display: block;
  margin-bottom: 5%;
}
</style>
