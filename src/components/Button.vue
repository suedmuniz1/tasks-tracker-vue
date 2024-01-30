<template>
  <button
    @click="$emit('toggle-add-task')"
    class="btn"
    :style="{ backgroundColor: color }"
  >
    {{ text }}
  </button>
</template>

<script>
  export default {
    name: "Button",
    props: {
      text: String,
      color: String,
    },
    emits: ["toggle-add-task"],
  };
</script>

<style scoped>
  button {
    border-radius: 10px;
    font-weight: bold;
    cursor: pointer;
  }
</style>
