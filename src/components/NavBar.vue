<template>
  <div class="header">
    <nav class="navbar">
      <h4 class="gradient-animation">Clique na tela para adicionar um bloco</h4>
      <h4 class="lastH4 gradient-animation">[Crtl + Click] para excluí-lo</h4>
    </nav>

    <button @click="printScreen" class="button">
      <img src="/images/photo-camera.png" />
    </button>
  </div>
</template>

<script>
import html2canvas from "html2canvas";

export default {
  name: "NavBar",
  methods: {
    printScreen() {
      html2canvas(document.body).then((canvas) => {
        var link = document.createElement("a");
        document.body.appendChild(link);

        link.download = "mindMap.png";
        link.href = canvas.toDataURL("image/png");
        link.target = "_blank";
        link.click();
      });
    },
  },
};
</script>

<style scoped>
.header {
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: space-between;

  width: 97%;
}

.button {
  padding: 8px;
  border-radius: 5px;

  background-color: rgb(24, 23, 23);

  border: none;
  cursor: pointer;
}

.button:hover {
  background-color: rgb(46, 45, 45);
}

.navbar {
  width: 400px;
  height: 80px;
  color: white;

  margin: 20px;
  padding: 15px;

  background-color: rgb(24, 23, 23);
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

.gradient-animation {
  background: -webkit-linear-gradient(left, #4fca67, #4f67ca);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>
