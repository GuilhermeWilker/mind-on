<template>
  <div>
    <nav class="navbar">
      <h4 class="gradient-animation">Clique na tela para adicionar um bloco</h4>
      <h4 class="lastH4 gradient-animation">[Crtl + Click] para excluí-lo</h4>
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
  text-align: center;

  z-index: 9999;
}

h4 {
  font-weight: 500;
  letter-spacing: 0.5px;
}

.navbar .lastH4 {
  padding: 5px 0;
}
.btn-seta {
  padding: 15px;
  border: none;
  color: white;

  background-color: #bfbcc5;
}
.gradient-animation {
  background: -webkit-linear-gradient(left, #4fca67, #4f67ca);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>
