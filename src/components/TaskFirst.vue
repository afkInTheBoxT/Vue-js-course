<template>
  <div class='list'>
    <h2>{{ titleList }} </h2>
    <select
      v-model="localBreeds"
      multiple
      size="30"
      @change="OnSelectChange"
    >
      <DogOption
        v-for="breed of Object.keys(breeds)"
        :key="breed.id"
        v-bind:breed="breed"
      />
    </select>
  </div>
</template>

<script>
import DogOption from "@/components/DogOption";

export default {
  components: {
    DogOption,
  },
  props: {
    titleList: {
      default: 'Звичайний заголовок'
    },
  },
  mounted() {
    fetch("https://dog.ceo/api/breeds/list/all")
      .then((response) => response.json())
      .then((json) => {
        this.breeds = json.message;
      });
  },
  data() {
    return {
      breeds: [],
      localBreeds: [],
    };
  },
  methods: {
    OnSelectChange() {
      this.$emit('change', this.localBreeds);
    }
  }
};
</script>

<style>
</style>