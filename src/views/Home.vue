<template>
  <AddTask v-show="showAddTask" @add-task="addTask" />
  <Tasks
    @toggle-reminder="toggleReminder"
    @delete-task="deleteTask"
    :tasks="tasks"
  />
</template>

<script>
  import Tasks from "../components/Tasks.vue";
  import AddTask from "../components/AddTask.vue";
  import axios from "axios";

  export default {
    name: "Home",
    props: {
      showAddTask: Boolean,
    },
    components: {
      Tasks,
      AddTask,
    },
    data() {
      return {
        tasks: [],
      };
    },
    methods: {
      async toggleReminder(task) {
        await axios.put(`backendAPI/tasks/${task.id}`, task).catch((error) => {
          console.error(error);
        });
      },
      async addTask(task) {
        const taskToAdd = await axios
          .post("backendAPI/tasks", task)
          .then((response) => {
            const { data } = response;
            return data;
          });

        this.tasks = [...this.tasks, taskToAdd];
      },
      async deleteTask(id) {
        await axios
          .delete(`backendAPI/tasks/${id}`)
          .catch((error) => {
            alert("Error when deleting task!");
            console.log(error);
          })
          .finally(() => {
            this.tasks = this.tasks.filter((task) => task.id !== id);
          });
      },
      async fetchTasks() {
        await axios
          .get("backendAPI/tasks")
          .then((response) => {
            const { data } = response;
            this.tasks = data;
          })
          .catch((error) => {
            console.error(error);
          });
      },
      async fetchTask(id) {
        const task = await axios
          .get(`backendAPI/tasks/${id}`)
          .then((response) => {
            const { data } = response;
            return data;
          })
          .catch((error) => {
            console.error(error);
          });

        return task;
      },
    },
    async created() {
      await this.fetchTasks();
    },
  };
</script>
