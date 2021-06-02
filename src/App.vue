<template>
  <div id="app">
    <HelloWorld msg="Yahtzee scoreblad" />
    <Score v-bind="" />
    <DiceRoll @clicked="passData" />
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
  methods: {
    passData(payload) {
      this.rolledNumbers = payload;
    },
  },
  data() {
    return {
      rolledNumbers: [],
    };
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
