<script>
import { mapActions } from "pinia";
import useMindMapStore from "../stores/mindMap";
import NavBar from "../components/NavBar.vue";

let backgroundImageUrl = 'url("/images/grid.png")';

export default {
  data() {
    return {};
  },
  components: {
    NavBar,
  },
  methods: {
    ...mapActions(useMindMapStore, ["createMindMap"]),
    addMindMap(e) {
      this.createMindMap(e);
    },
  },
};
</script>

<template>
  <NavBar />

  <div
    @click="addMindMap"
    class="board"
    :style="{ backgroundImage: `url(${backgroundImageUrl})` }"
  ></div>
</template>

<style scoped>
.board {
  width: 100vw;
  height: 100vh;
  overflow-x: hidden;
}
</style>
