<template>
  <div
    @click="addMentalBlock"
    class="app"
    :style="{ backgroundImage: `url(${backgroundImageUrl})` }"
  >
    <canvas ref="canvas" class="canvas"></canvas>
  </div>
</template>

<script>
import { mapActions } from "pinia";
import useMentalBlockStore from "./stores/mentalBlock";

export default {
  data() {
    return {
      backgroundImageUrl: "",
    };
  },
  methods: {
    ...mapActions(useMentalBlockStore, ["createMentalBlock"]),

    addMentalBlock(e) {
      this.createMentalBlock(e);
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
