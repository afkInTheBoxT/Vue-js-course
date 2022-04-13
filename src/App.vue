<template>
  <div>
    <TaskFirst
      class="list task4Class"
      titleList="Test"
      v-on:change="OnSelectChange"
    />

    <FilledList class="list" v-bind:breeds="selectedBreeds" />

    <CustomList
      v-bind:breeds="breeds"
      :selectedBreeds="selectedBreeds"
      v-on:change="OnCustomSelectChange"
    />
  </div>
</template>

<script>
import TaskFirst from "@/components/TaskFirst";
import FilledList from "@/components/FilledList";
import CustomList from "@/components/CustomList";

export default {
  name: "App",
  components: {
    TaskFirst,
    FilledList,
    CustomList,
  },
  data() {
    return {
      selectedBreeds: [],
      breeds: [],
    };
  },
  mounted() {
    fetch("https://dog.ceo/api/breeds/list/all")
      .then((response) => response.json())
      .then((json) => {
        this.breeds = json.message;
      });
  },
  methods: {
    OnSelectChange(value) {
      if (value instanceof Event) {
        return;
      }
      this.selectedBreeds = value;
    },
    OnCustomSelectChange(value) {
      let clickedBreedIndex = this.selectedBreeds?.indexOf(value);
      if (clickedBreedIndex != null && clickedBreedIndex < 0) {
        this.selectedBreeds.push(value);
      } else {
        this.selectedBreeds.splice(clickedBreedIndex, 1);
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.list {
  float: left;
  padding: 20px;
}

select {
  min-width: 200px;
}

.task4Class {
  color: green;
}
</style>
