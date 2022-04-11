<template>
  <li :class="{ hasSubBreeds: breed[1]?.length > 0 }">
    {{ breed[0] }}
  </li>
</template>

<script>
export default {
  props: {
    breed: {
      key: Object,
    },
  },
};
</script>

<style>
.hasSubBreeds {
  color: red;
}
</style>