/* Crear estado inicial */
<template>
  <section class="src-components-container">
    <div class="jumbotron">
      <Square
        @winnerSquare="checkWinner($event)"
        :colorStyle="color"
        v-for="(color, index) in coloresContainer"
        :key="index"
      />
    </div>
  </section>
</template>

<script>
import Square from "./Square.vue";

export default {
  name: "src-components-container",
  components: {
    Square,
  },
  props: ["coloresContainer", "winnerColorContainer"],
  mounted() {},
  updated() {},
  data() {
    return {
    };
  },
  methods: {
    checkWinner(colorStyle) {
      // console.log("checkWinner() " + colorStyle);
      if (colorStyle == this.winnerColorContainer) {
        console.log("Ganaste");
        this.$emit("changeMessageNavigator", true);
      }else{
        this.$emit("changeMessageNavigator", false);
      }
    },
    
  },

  computed: {},
};
</script>

<style scoped lang="css">
.src-components-container {
  margin: 20px auto;
  max-width: 600px;
  background-color: #232323;
}
.jumbotron {
  background-color: #232323;
  color: #232323;
}
</style>
