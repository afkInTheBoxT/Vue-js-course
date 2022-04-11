<template>
  <div>
    <h2>Task 3-4</h2>
    <p class="all" @click="open">Список пород (натисніть, щоб розгорнути):</p>
    <div
      class="hideContent accordion"
      :class="{ accordiooon: isHide == false }"
    >
      <div v-if="isHide == false">
        <ul>
          <DogBreedElement
            v-for="breed of Object.entries(breeds)"
            :key="breed.id"
            v-bind:breed="breed"
          />
        </ul>
      </div>
    </div>

    <RandomBreed v-bind:breeds="Object.entries(breeds)" />
  </div>
</template>


<script>
import DogBreedElement from "@/components/DogBreedElement";
import RandomBreed from "@/components/RandomBreed";

export default {
  data() {
    return {
      isHide: true,
    };
  },
  props: ["breeds", "myBreeds"],
  components: {
    DogBreedElement,
    RandomBreed,
  },
  methods: {
    open() {
      this.isHide = !this.isHide;
    },
  },
};
</script>

<style>
ul {
  list-style-type: none;
}
.pos {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.all {
  background: rgb(215, 250, 215);
  width: 400px;
  height: 40px;
  margin: 20px auto;
}

h1,
h2 {
  margin: 0;
  padding: 0;
  text-align: center;
  vertical-align: middle;
}

.hideContent {
  background: rgb(215, 250, 215);
  width: 300px;
  margin: 20px auto;
}

.accordion {
  overflow: hidden;
  height: 0px;
  transition: all 1s;
}

.accordiooon {
  transition: all 1s;
  height: 100%;
}
</style>