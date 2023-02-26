<script>
import { mapActions } from "pinia";
import useMentalBlockStore from "../stores/mentalBlock";
export default {
  data() {
    return {};
  },
  methods: {
    ...mapActions(useMentalBlockStore, ["createMentalBlock"]),
    addMentalBlock(e) {
      this.createMentalBlock(e);
    },
  },
};
</script>

<template>
  <div
    @click="addMentalBlock"
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
