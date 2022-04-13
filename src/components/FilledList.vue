<template>
  <div class="list">
    <h2>{{ titleList }} </h2>
    <select v-model="localBreeds" multiple size="30">
      <DogOption v-for="breed of breeds" :key="breed" v-bind:breed="breed" />
    </select>
  </div>
</template>

<script>
import DogOption from "@/components/DogOption";

export default {
  props: {
    breeds: [],
    titleList: {
      default: "Звичайний заголовок",
    },
  },
  components: {
    DogOption,
  },
  data() {
    return {
      localBreeds: [],
    };
  },
};
</script>

<style>
</style>