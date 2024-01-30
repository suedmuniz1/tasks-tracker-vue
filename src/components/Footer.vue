<template>
  <footer>
    <p>
      Made by
      <a href="https://github.com/suedmuniz1" target="_blank"
        >Sued Nepomuceno</a
      >
    </p>
    <router-link to="/about">About</router-link>
  </footer>
</template>

<script>
  export default {
    name: "Footer",
  };
</script>

<style scoped>
  a {
    color: #333;
  }

  footer {
    margin-top: 30px;
    text-align: center;
  }
</style>
