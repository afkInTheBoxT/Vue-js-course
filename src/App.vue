<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />

    <TaskFirst v-bind:name="name" />

    <TaskSecond v-bind:breeds="breeds" />

    <TaskThird
      v-bind:breeds="myBreeds"
      :myBreeds="myBreeds"
      v-on:add-random="AddRandom"
      v-on:remove-random="RemoveRandom"
      v-on:shuffle="Shuffle"
    />
  </div>
</template>

<script>
import TaskFirst from "@/components/TaskFirst";
import TaskSecond from "@/components/TaskSecond";
import TaskThird from "@/components/TaskThird";

export default {
  name: "App",
  data() {
    return {
      name: '',
      breeds: [],
      myBreeds: [],
      allBreedsList: [],
    };
  },
  mounted() {
    fetch("https://dog.ceo/api/breeds/list/all")
      .then((response) => response.json())
      .then((json) => {
        this.breeds = json.message;
        this.allBreedsList = Object.entries(json.message);
        this.myBreeds = Object.entries(json.message).slice(0, 5);
      });
  },
  components: {
    TaskFirst,
    TaskSecond,
    TaskThird,
  },
  methods: {
    AddRandom() {
      let element =
        this.allBreedsList[
          Math.floor(Math.random() * this.allBreedsList.length)
        ];
      this.myBreeds.push(element);
    },
    RemoveRandom() {
      this.myBreeds.splice(
        Math.floor(Math.random() * this.myBreeds.length),
        1
      );
    },
    Shuffle(array) {
      for (var i = array.length - 1; i > 0; i--) {
        var j = Math.floor(Math.random() * (i + 1));
        var temp = array[i];
        array[i] = array[j];
        array[j] = temp;
      }
    },
  }
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
</style>
