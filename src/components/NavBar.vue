<template>
  <div>
    <nav class="navbar">
      <h3>Mind On</h3>
    </nav>
  </div>
</template>

<script>
export default {
  name: "NavBar",
};
</script>

<style scoped>
.navbar {
  position: fixed;
  width: 400px;
  height: 80px;
  color: white;

  margin: 20px;
  padding: 15px;

  background-color: black;
  border-radius: 5px;

  z-index: 9999;
}

.btn-seta {
  padding: 15px;
  border: none;
  color: white;

  background-color: #bfbcc5;
}
</style>
