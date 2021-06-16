<template>
  <div id="app">
    <h1>Yahtzee scoreblad</h1>
    <Score />
    <DiceRoll />
  </div>
</template>

<script>
import DiceRoll from "./components/DiceRoll.vue";
import Score from "./components/Score.vue";

export default {
  name: "App",
  components: {
    DiceRoll,
    Score,
  },
  methods: {},
  data() {
    return {};
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  margin-top: 40px;
}
</style>
