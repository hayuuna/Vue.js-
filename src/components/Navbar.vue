<template>
  <nav class="navbar">
    <a href="#">Home</a>
    <a href="#">Movies</a>
    <a href="#">About</a>
  </nav>
</template>

<script>
  export default {
    name: 'NavbarComponent', //컴포넌트 명 _ Component
  }
</script>

<style>
  .navbar {
    background: #000;
    padding: 20px;
  }

  .navbar a {
    color: #fff;
    text-decoration: none;
    padding: 1em;
  }
</style>