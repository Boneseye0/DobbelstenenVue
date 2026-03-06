<script setup>
import { computed, ref } from 'vue';
import RollDice from './components/RollDice.vue';

const diceRolled = ref([1, 2, 3, 4, 5, 6]);

const updateDiceRolled = (diceValues) => {
  diceRolled.value = (diceValues)
}

const computedDiceCount = computed(() => { 
  const diceCount = {
    1 : 0,
    2 : 0,
    3 : 0,
    4 : 0,
    5 : 0,
    6 : 0,
  };

  diceRolled.value.forEach(value => diceCount[value]++);

  return diceCount;
})
 
</script>

<template>
 
  <div>
    <RollDice @throw="updateDiceRolled" />
   <br>
    <table>
      <thead>
        <tr>
        <td>Getal</td><td>aantal</td>
      </tr>
    </thead>
      <tbody  v-for="(value, key) in computedDiceCount" class="dice">
        <tr>
          <td class="dice">{{ key }}</td><td class="dice">{{ value }}</td>
        </tr>
      </tbody>
      
    </table>
    <br>
    <table>
    <thead>
      <tr>
        <td>Getal</td><td>aantal</td>
      </tr>
    </thead>
    <tbody>
      <tr><td>1</td><td>{{ computedDiceCount[1] }}</td></tr>
      <tr><td>2</td><td>{{ computedDiceCount[2] }}</td></tr>
      <tr><td>3</td><td>{{ computedDiceCount[3] }}</td></tr>
      <tr><td>4</td><td>{{ computedDiceCount[4] }}</td></tr>
      <tr><td>5</td><td>{{ computedDiceCount[5] }}</td></tr>
      <tr><td>6</td><td>{{ computedDiceCount[6] }}</td></tr>
    </tbody>
    </table>
  </div>

</template>

<style scoped>
table {
  margin-inline: auto;
  border-collapse: collapse;
  width: 200px;
  border: 1px solid black;
 }

thead {
  border: 2px solid black;
  text-align: center;
  }

tbody {
  border: 1px solid black;
  padding:  top 5px right 15px;
  text-align: left;
}

td { 
  border: 1px solid black;
}

.dice {
  border: 1px solid black;
  text-align: right;  
}
</style>
