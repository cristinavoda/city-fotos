<template>
  <form>
    <div class="flex">
      <div class="flex-col">
        <label>city name</label>
        <input type="text" name="city" v-model="city"/>
      </div>
      <div class="flex-col">
        <label>city image</label>
        <input type="text" name="image" v-model="image" />
      </div>
    </div>
    <div class="flex-col">
      <label>about this city..</label>
      <textarea typeof="text" name="about" v-model="about"></textarea>
    </div>
    <button @click.prevent="submitCity">submit</button>
  </form>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      city: "",
      image: "",
      about: "",
    };
  },
  methods: {
    submitCity() {
      this.$emit("sendCitytoApp", {
        name: this.city,
        about: this.about,
        image: this.image,
      });
      this.city = "";
      this.about = "";
      this.image = "";
    },
  },
};
</script>

<style>
form {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  margin-top: 2rem;
}
form button {
  align-self: center;
}

.flex {
  display: flex;
  justify-content: space-between;
  margin-left: 20%;
  margin-right: 20%;
}
.flex-col {
  display: flex;
  flex-direction: column;
}
</style>
