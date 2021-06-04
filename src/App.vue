<template>
  <div id="app">
    <HelloWorld msg="Yahtzee scoreblad" />
    <Score />
    <DiceRoll />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import DiceRoll from "./components/DiceRoll.vue";
import Score from "./components/Score.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
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
