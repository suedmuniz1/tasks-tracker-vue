<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      v-show="showAddTaskButton"
      @toggle-add-task="$emit('toggle-add-task')"
      :text="showAddTask ? 'Close' : 'Add Task'"
      :color="showAddTask ? '#960200' : '#00A676'"
      :showAddTask="showAddTask"
    />
  </header>
</template>

<script>
  import Button from "./Button.vue";

  export default {
    name: "Header",
    props: {
      title: String,
      showAddTask: Boolean,
    },
    components: {
      Button,
    },
    emits: ["toggle-add-task"],
    computed: {
      showAddTaskButton() {
        return this.$route.path === "/";
      },
    },
  };
</script>

<style scoped>
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
</style>
