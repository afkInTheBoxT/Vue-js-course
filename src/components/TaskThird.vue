<template>
  <div>
      <hr>
      <h2>Task 5</h2>
    <div>
      <button v-on:click="$emit('add-random', breeds)">
        Додати випадкову породу
      </button>
      <button v-on:click="$emit('remove-random', breeds)">
        Видалити випадкову породу
      </button>
      <button v-on:click="$emit('shuffle', breeds)">Перемішати список</button>

      <ul>
        <DogBreedElement
          v-for="breed of breeds"
          :key="breed[0]"
          v-bind:breed="breed"
        />
      </ul>
    </div>
  </div>
</template>


<script>
import DogBreedElement from "@/components/DogBreedElement";

export default {
  props: ["breeds"],
  components: {
    DogBreedElement,
  },
};
</script>

<style>
ul {
  list-style-type: none;
}
</style>