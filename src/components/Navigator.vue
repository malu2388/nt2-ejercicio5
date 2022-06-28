<template>
  <section class="src-components-navigator">
    <div>
      <span class="button onHover" @click="restart()">
        New Colors!</span
      >
      <span class="message">{{ message }}</span>
      <button class="button onHover" @click="startEasy()">
        easy
      </button>
      <button class="button onHover" @click="startHard()">
        hard
      </button>
      <Container
        :coloresContainer="coloresNavigator"
        :winnerColorContainer="winnerColorNavigator"
        @changeMessageNavigator="changeMessage($event)"
      />
    </div>
  </section>
</template>

<script>
import Container from "./Container.vue";

export default {
  name: "src-components-navigator",
  components: {
    Container,
  },
  props: [],
  mounted() {
    this.generarColores();
  },
  data() {
    return {
      coloresNavigator: [],
      winnerColorNavigator: "",
      colorCount: 6,
      message: "",
    };
  },
  methods: {
    mouseOver() {
      console.log("Cambiar estilo");
    },

    startEasy() {
      this.colorCount = 3;
      this.restart();
    },

    startHard() {
      this.colorCount = 6;
      this.restart();
    },

    createRandomStringColor() {
      var newColor =
        "rgb(" +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ")";
      return newColor;
    },

    randomInt() {
      return Math.floor(Math.random() * 256);
    },
    generarColores() {
      this.coloresNavigator = [];
      for (let i = 0; i < this.colorCount; i++) {
        this.coloresNavigator.push(this.createRandomStringColor());
      }
      this.winnerColorNavigator = this.PickWinner();
      this.$emit("winnerColorNavigatorEmit", this.winnerColorNavigator);
    },

    PickWinner() {
      return this.coloresNavigator[Math.floor(Math.random() * this.colorCount)];
    },

    changeMessage(win) {
      // console.log("changeMessage()");
      // console.log("Gano: " + win);
      if (win) {
        this.message = "You Picked Right!";
        this.setAllColorsTo(this.winnerColorNavigator);
        //	header.style.backgroundColor = pickedColor;
      } else {
        this.message = "Try Again!";
      }
    },

    restart() {
      this.generarColores();
      this.message = "";
      // header.style.backgroundColor = "steelblue";
    },

    setAllColorsTo(winnerColorNavigator) {
      this.coloresNavigator = [];
      for (let i = 0; i < this.colorCount; i++) {
        this.coloresNavigator.push(winnerColorNavigator);
      }
    },
  },

  computed: {},
};
</script>

<style scoped lang="css">
.src-components-navigator {
  background-color: #ffffff;
  height: 30px;
  text-align: center;
  margin: 0;
  margin-top: -30px;
}


.button {
  border: none;
  background-color: white;
  font-family: "Montserrat", "Avenir";
  text-transform: uppercase;
  height: 100%;
  font-weight: 700;
  letter-spacing: 1px;
  color: steelblue;
  transition: all 0.3s;
  outline: none;
  margin: 0 25 0 25;
}

.onHover:hover {
  background-color: steelblue;
  color: white;
}

.message{
  color: steelblue;
  margin: 25px;
}
</style>
