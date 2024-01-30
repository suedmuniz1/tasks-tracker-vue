<template>
  <div class="container">
    <Header
      @toggle-add-task="toggleAddTask"
      title="Task Tracker"
      :showAddTask="showAddTask"
    />
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</template>

<script>
  import Header from "./components/Header.vue";
  import Footer from "./components/Footer.vue";
  import Tasks from "./components/Tasks.vue";
  import AddTask from "./components/AddTask.vue";

  export default {
    name: "App",
    components: {
      Header,
      Footer,
      Tasks,
      AddTask,
    },
    data() {
      return {
        showAddTask: false,
      };
    },
    methods: {
      toggleAddTask() {
        this.showAddTask = !this.showAddTask;
      },
    },
  };
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 60px;
    display: flex;
    justify-content: center;
  }

  .container {
    border: 1px solid gray;
    border-radius: 10px;
    padding: 20px;
    width: 600px;
  }

  .btn {
    width: 100px;
    padding: 10px;
    background-color: black;
    color: white;
    border: none;
  }
</style>
