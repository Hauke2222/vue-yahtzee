<template>
  <div id="diceRollTemplate">
    <hr />
    <div
      style="font-size: 32px"
      v-for="(n, index) in rolledNumbers"
      :key="index"
    >
      {{ unicodes[index - 1] + ": " + n }}
    </div>
    <br />
    <button
      @click="
        rollDice();
        passDataToScoreComponent();
      "
    >
      Rol dobbelstenen
    </button>
  </div>
</template>

<script>
export default {
  name: "DiceRoll",

  props: {},

  methods: {
    passDataToScoreComponent() {
      this.$root.$emit("clicked", this.rolledNumbers, this.dices);
      //this.$root.$emit("clicked", this.dices);
    },

    rollDice() {
      this.resetRolledNumbers();
      for (let i = 0; i < this.numberOfDices; i++) {
        this.dices[i] = Math.floor(Math.random() * 6) + 1;
        this.rolledNumbers[this.dices[i]]++;
      }
    },
    resetRolledNumbers() {
      this.rolledNumbers = {
        1: 0,
        2: 0,
        3: 0,
        4: 0,
        5: 0,
        6: 0,
      };
    },
  },
  created() {
    this.resetRolledNumbers();
  },

  data() {
    return {
      dices: [],
      numberOfDices: 5,
      rolledNumbers: [],
      unicodes: ["\u2680", "\u2681", "\u2682", "\u2683", "\u2684", "\u2685"],
    };
  },
};
</script>

<style></style>
