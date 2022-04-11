<template>
  <div>
    <hr />
    <h2>Task 1 - 2</h2>
    <div>
      <p>Напишіть своє ім'я:</p>
      <NameForm @change-name="changeName" />
      <p>Привіт, {{ name ?? "Незнайомець" }}.</p>
    </div>
    <hr />
  </div>
</template>

<script>
import NameForm from "@/components/NameForm";

export default {
  data() {
    return {
      name: this.name,
    };
  },
  components: {
    NameForm,
  },
  methods: {
    changeName(newName) {
      this.name = newName.name;
    },
  },
};
</script>