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
          <td></td>
        </tr>
        <tr>
          <td>Carré</td>
          <td>Totaal van alle stenen</td>
          <td></td>
        </tr>
        <tr>
          <td>Full House</td>
          <td>25 punten</td>
          <td></td>
        </tr>
        <tr>
          <td>Kleine Straat</td>
          <td>30 punten</td>
          <td></td>
        </tr>
        <tr>
          <td>Grote Straat</td>
          <td>40 punten</td>
          <td></td>
        </tr>
        <tr>
          <td>Yahtzee</td>
          <td>50 punten</td>
          <td></td>
        </tr>
        <tr>
          <td>Chance</td>
          <td>Totaal 5 stenen</td>
          <td></td>
        </tr>
      </thead>
    </table>
  </div>
</template>

<script>
export default {
  name: "Score",

  methods: {},
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
</style>
