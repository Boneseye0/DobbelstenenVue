<script setup>
defineProps(
    {
        throwCount: Number,
    }
);
const emit = defineEmits([diceRolled]);

const emitevent = () =>{
    emit 
}
const rollDice = () =>{
    
    for (let index = 0; index < throwCount; index++) {
                const randomNumber = Math.ceil(Math.random() * 6);
                diceRolled.push(randomNumber);
                diceCount[randomNumber] ++;
        
    };
}
    
    </script>

    <template>
        <button @click="emitEvent"></button>
    </template>