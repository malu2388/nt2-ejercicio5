<template>
  <section class="src-components-header">
    <div class="jumbotron">
      <h1>
        The Great <br />
        <span id="colorDisplay">{{ winnerColorHeader }}</span>
        <br />
        Guessing Game
      </h1>
      <br /> 
     <!-- winnerColorNavigatorEmit se pasa del hijo (Navigator) al padre (Header) -->
     <Navigator @winnerColorNavigatorEmit="winnerColorHeader = $event" /> </div>
  </section>
</template>

<script>
import Navigator from "./Navigator.vue";

export default {
  name: "src-components-header",
  components: {
    Navigator,
  },
  props: [],
  mounted() {},
  data() {
    return {
      winnerColorHeader: "",
    };
  },
  methods: {},
  computed: {},
};
</script>

<style scoped lang="css">
.src-components-header {
  transition: all 0.3s;
  background: steelblue;
  text-transform: uppercase;
  text-align: center;
  margin: 0;
  color: white;
}

h1 {
  font-weight: normal;
  line-height: 1.1;
  padding: 20px 0;

}
</style>
