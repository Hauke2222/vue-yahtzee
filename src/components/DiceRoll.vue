<template>
  <div id="diceRollTemplate">
    <hr />
    <div
      style="font-size: 32px"
      v-for="(n, index) in rolledNumbers"
      :key="index"
    >
      {{ n.unicode + ": " + n.value }}
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
      this.$root.$emit("clicked", this.rolledNumbers);
    },

    rollDice() {
      this.resetRolledNumbers();
      for (let i = 0; i < this.numberOfDices; i++) {
        this.dices[i] = Math.floor(Math.random() * 6) + 1;
        this.rolledNumbers[this.dices[i] - 1].value++;
      }
    },
    resetRolledNumbers() {
      this.rolledNumbers = [
        { eyes: 1, value: 0, unicode: "\u2680" },
        { eyes: 2, value: 0, unicode: "\u2681" },
        { eyes: 3, value: 0, unicode: "\u2682" },
        { eyes: 4, value: 0, unicode: "\u2683" },
        { eyes: 5, value: 0, unicode: "\u2684" },
        { eyes: 6, value: 0, unicode: "\u2685" },
      ];
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
    };
  },
};
</script>

<style></style>
