<template>
  <div
    @click="addMentalBlock"
    class="board"
    :style="{ backgroundImage: `url(${backgroundImageUrl})` }"
  >
    <NavBar />

    <canvas ref="canvas" class="canvas"> </canvas>
  </div>
</template>

<script>
import { mapActions } from "pinia";
import NavBar from "./components/NavBar.vue";
import useMentalBlockStore from "./stores/mentalBlock";
export default {
  components: {
    NavBar,
  },
  data() {
    return {
      backgroundImageUrl: "",
      // isDrawing: false,
      // startX: null,
      // startY: null,
    };
  },
  methods: {
    ...mapActions(useMentalBlockStore, ["createMentalBlock"]),
    addMentalBlock(e) {
      this.createMentalBlock(e);
    },
    // handleKeyDown(e) {
    //   if (e.code === "space") {
    //     window.addEventListener("click", this.handleMouseClick);
    //   }
    // },
    // handleMouseClick(e) {

    // },
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

    // Linhas do autor
    // ctx.lineWidth = 4;
    // ctx.strokeStyle = "#000000";

    // window.addEventListener("keydown", this.handleKeyDown);
  },
};
</script>

<style>
.board {
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
