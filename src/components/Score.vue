<template>
  <div id="scoreTemplate">
    <br />
    <table>
      <thead>
        <tr>
          <th>Bovenste helft</th>
          <th>Punten Telling</th>
          <th>Spel 1</th>
        </tr>
        <tr>
          <td>Enen</td>
          <td>Totaal alle enen</td>
          <td></td>
        </tr>
        <tr>
          <td>Tweeën</td>
          <td>Totaal alle tweeën</td>
          <td></td>
        </tr>
        <tr>
          <td>Drieën</td>
          <td>Totaal alle drieën</td>
          <td></td>
        </tr>
        <tr>
          <td>Vieren</td>
          <td>Totaal alle vieren</td>
          <td></td>
        </tr>
        <tr>
          <td>Vijven</td>
          <td>Totaal alle vijven</td>
          <td></td>
        </tr>
        <tr>
          <td>Zessen</td>
          <td>Totaal alle zessen</td>
          <td></td>
        </tr>
      </thead>
    </table>
    <table>
      <thead>
        <tr>
          <th>Onderste helft</th>
          <th>Punten Telling</th>
          <th>Spel 1</th>
        </tr>
        <tr>
          <td>3 of a kind</td>
          <td>Totaal van alle stenen</td>
          <td id="align-right">{{ threeOfAKind }}</td>
        </tr>
        <tr>
          <td>Carré</td>
          <td>Totaal van alle stenen</td>
          <td id="align-right">{{ fourOfAKind }}</td>
        </tr>
        <tr>
          <td>Full House</td>
          <td>25 punten</td>
          <td id="align-right">{{ fullHouse }}</td>
        </tr>
        <tr>
          <td>Kleine Straat</td>
          <td>30 punten</td>
          <td id="align-right">{{ smallStraight() }}</td>
        </tr>
        <tr>
          <td>Grote Straat</td>
          <td>40 punten</td>
          <td id="align-right">{{ largeStraight() }}</td>
        </tr>
        <tr>
          <td>Yahtzee</td>
          <td>50 punten</td>
          <td id="align-right">{{ yahtzee }}</td>
        </tr>
        <tr>
          <td>Chance</td>
          <td>Totaal 5 stenen</td>
          <td id="align-right">{{ sumOfRolledNumbers }}</td>
        </tr>
      </thead>
    </table>
  </div>
</template>

<script>
export default {
  name: "Score",

  methods: {
    //calculateTopSide() {},

    smallStraight() {
      //return ["1234", "2345", "3456"].includes(this.dicesString) ? 30 : 0;

      let x = /1234|2345|3456/.test(this.dicesString().replace(/(.)\1/, "$1"));
      return x ? 30 : 0;
    },

    largeStraight() {
      let x = /12345|23456/.test(this.dicesString().replace(/(.)\1/, "$1"));
      return x ? 40 : 0;
    },
    dicesString() {
      return this.dices
        .slice()
        .sort()
        .join("");
    },
  },

  props: {},

  computed: {
    sumOfRolledNumbers() {
      // return this.rolledNumbers
      //   .map((this.rolledNumber) => rolledNumber.value * rolledNumber.eyes)
      //   .reduce((total, amount) => total + amount, 0);
      let sum = 0;
      for (const item in this.rolledNumbers) {
        sum += this.rolledNumbers[item] * item;
      }
      return sum;
    },

    threeOfAKind() {
      if (Object.values(this.rolledNumbers).find((element) => element >= 3)) {
        return this.sumOfRolledNumbers;
      }
      return 0;
    },

    fourOfAKind() {
      if (Object.values(this.rolledNumbers).find((element) => element >= 4)) {
        return this.sumOfRolledNumbers;
      }
      return 0;
    },

    fullHouse() {
      if (
        Object.values(this.rolledNumbers).find((element) => element == 3) &&
        Object.values(this.rolledNumbers).find((element) => element == 2)
      ) {
        return 25;
      }
      return 0;
    },

    yahtzee() {
      if (Object.values(this.rolledNumbers).find((element) => element == 5)) {
        return this.sumOfRolledNumbers;
      }
      return 0;
    },
  },

  mounted() {
    this.$root.$on("clicked", (rolledNumbers, dices) => {
      this.rolledNumbers = rolledNumbers;
      this.dices = dices;
    });
  },

  data() {
    return {
      rolledNumbers: [],
      dices: [],
    };
  },
};
</script>

<style>
#scoreTemplate {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
table {
  text-align: left;
  margin: 24px;
}

th,
td {
  border: 1px solid lightgray;
  text-align: left;
}
#align-right {
  text-align: right;
}
</style>
