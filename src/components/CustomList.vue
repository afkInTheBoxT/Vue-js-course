<template>
  <div class="selectList list">
    <div class="list-elements">
      <div
        class="list-element"
        v-for="breed of Object.keys(breeds)"
        :key="breed"
        @click="OnSelectChange"
      >
        {{ breed }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    breeds: [],
    selectedBreeds: [],
  },
  components: {},
  mounted() {},
  methods: {
    OnSelectChange(value) {
      let clickedBreed = value.target.innerHTML;
      value.target.classList.toggle("list-element-selected");
      this.$emit("change", clickedBreed);
    },
  },
};
</script>

<style>
.selectList {
  border: 1px solid black;
  min-height: 500px;
  max-height: 500px;
  min-width: 200px;
  overflow: scroll;
}

.list-element {
  background-color: rgb(226, 226, 226);
  border: 1px rgb(239, 239, 239);
  color: rgb(18, 18, 18);
}

.list-element-selected {
  background-color: rgb(6, 92, 177);
  color: white;
}
</style>