<script setup>
import { computed, ref } from 'vue';
//import RollDice from './components/RollDice.vue'

let throwCount = ref('6')

let diceRolled = ref([]);

const rollDice = () =>{
    diceRolled.value = [];    
for (let index = 0; index < throwCount.value; index++) {
  const randomNumber = Math.ceil(Math.random() * 6);
                      diceRolled.value.push(randomNumber);}
}

const computedDiceCount = computed(() => { const diceCount = {
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
 /*                 
let computedDiceCount = computed(() => {
  for (let index = 0; index < diceRolled.value.length; index++) {
  diceCount[diceRolled.value[index]] ++;
  }
})
let diceCount = {
  1: 0,
  2: 0,
  3: 0,
  4: 0,
  5: 0,
  6: 0,
};
  */
</script>

<template>
  <div>
   <input type="number" v-model="throwCount"><br>
   <button @click="rollDice">Throw</button>

   <br>
    <p>{{ diceRolled }}</p>
    <ul>
      <li v-for="(value, key, index) in computedDiceCount">
      {{ key }} : {{ value }}
      </li>
      
    </ul>
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

</style>
