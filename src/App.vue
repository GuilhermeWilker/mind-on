<template>
  <div
    @click="addDiv"
    class="app"
    :style="{ backgroundImage: 'url(' + backgroundImageUrl + ')' }"
  >
    <canvas ref="canvas" class="canvas"></canvas>
  </div>
</template>

<script>
export default {
  data() {
    return {
      backgroundImageUrl: "",
    };
  },
  methods: {
    addDiv(event) {
      // Obter as coordenadas X e Y do clique
      const x = event.clientX - 138;
      const y = event.clientY - 60;

      // Criar um novo elemento div e configurar sua posição e estilo
      const newDiv = document.createElement("div");
      newDiv.style.position = "absolute";
      newDiv.style.left = x + "px";
      newDiv.style.top = y + "px";
      newDiv.style.width = "276px";
      newDiv.style.height = "120px";
      newDiv.style.backgroundColor = "white";
      newDiv.style.boxShadow = "3px 4px 12px 2px rgba(0, 0, 0, 0.25)";
      newDiv.style.borderRadius = "10px";

      // Adicionar um novo elemento input dentro da div
      const newInput = document.createElement("input");
      newInput.style.width = "100%";
      newInput.style.height = "100%";
      newInput.style.border = "none";
      newInput.style.background = "none";
      newInput.style.outline = "none";
      newInput.style.fontFamily = "Arial";
      newInput.style.fontSize = "18px";
      newInput.style.textAlign = "center";

      newDiv.appendChild(newInput);

      // Adicionar a nova div ao DOM
      document.body.appendChild(newDiv);

      // Colocar o foco no novo input para que o usuário possa começar a digitar imediatamente
      newInput.focus();

      // Adicionar um ouvinte de eventos para o clique na nova div
      newDiv.addEventListener("click", (event) => {
        // Verificar se a tecla Ctrl está pressionada
        if (event.ctrlKey) {
          // Excluir a div do DOM
          document.body.removeChild(newDiv);
        }
      });
    },
  },
  mounted() {
    const canvas = document.createElement("canvas");
    canvas.width = 50;
    canvas.height = 50;
    const ctx = canvas.getContext("2d");

    // Desenhar linhas horizontais
    for (let y = 0; y < canvas.height; y += 70) {
      ctx.beginPath();
      ctx.moveTo(0, y);
      ctx.lineTo(canvas.width, y);
      ctx.strokeStyle = "#CCCCCC";
      ctx.stroke();
    }

    // Desenhar linhas verticais
    for (let x = 0; x < canvas.width; x += 70) {
      ctx.beginPath();
      ctx.moveTo(x, 0);
      ctx.lineTo(x, canvas.height);
      ctx.strokeStyle = "#CCCCCC";
      ctx.stroke();
    }

    // Converter o canvas em uma imagem de dados de URL
    const dataUrl = canvas.toDataURL();

    // Definir a imagem de fundo da div pai
    this.backgroundImageUrl = dataUrl;
  },
};
</script>

<style>
.app {
  width: 100vw;
  height: 100vh;

  overflow-x: hidden;
}

.canvas {
  position: absolute;
  width: 100%;
  height: 100%;
}
</style>
