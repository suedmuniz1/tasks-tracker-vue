<template>
  <div
    @dblclick="onToggleReminder(task)"
    :class="`task ${task.reminder ? 'reminder' : ''}`"
  >
    <h3>
      {{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times" />
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
  export default {
    name: "Task",
    props: {
      task: Object,
    },
    methods: {
      onToggleReminder(task) {
        this.task.reminder = !this.task.reminder;
        this.$emit("toggle-reminder", task);
      },
    },
  };
</script>

<style scoped>
  .task {
    background: #f4f4f4;
    padding: 5px 10px;
    margin-bottom: 5px;
    cursor: pointer;
  }

  .task.reminder {
    border-left: 5px solid green;
  }

  h3 {
    display: flex;
    justify-content: space-between;
  }

  .fas {
    color: red;
  }
</style>
