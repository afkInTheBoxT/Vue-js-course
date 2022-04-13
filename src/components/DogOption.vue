<template>
  <option>
    {{ breed }}
  </option>
</template>

<script>
export default {
  props: {
    breed: {
      key: Object,
    }
  },
};
</script>

<style>
.hasSubBreeds {
  color: red;
}
</style>