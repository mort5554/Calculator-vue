<script setup>
import { ref } from 'vue';

const screen = ref("")
const previousNumber = ref()
const currentNumber = ref()
const firstNumbersArray = ref([])
let operator

function addNumber(num){
    if(firstNumbersArray.value.length > 12){
        alert("Too lot of numbers")
    }
    screen.value += num
    firstNumbersArray.value.push(num)
    currentNumber.value = screen.value
}
function opUsed(op){
    previousNumber.value = currentNumber.value
    currentNumber.value = ""
    screen.value = ''
    return operator = op
}
function equation(){
    let outcome
    if(operator === "+"){
        outcome = parseFloat(previousNumber.value) + parseFloat(currentNumber.value)
        screen.value = outcome
    }
    else if(operator === "-"){
        outcome = parseFloat(previousNumber.value) - parseFloat(currentNumber.value)
        screen.value = outcome
    }
    else if(operator === "x"){
        outcome = parseFloat(previousNumber.value) * parseFloat(currentNumber.value)
        screen.value = outcome
    }
    else if(operator === "/"){
        outcome = parseFloat(previousNumber.value) / parseFloat(currentNumber.value)
        screen.value = outcome
    }
}
function deleteLastNumber(){
    screen.value = screen.value.toString().slice(0, -1)
    currentNumber.value = currentNumber.value.toString().slice(0, -1)
}
</script>

<template>
    <title>Calculator</title> 
<main class="calculatorContainer">
        <div class="calculatorScreenContainer">
            <div id="calculatorScreen">
                <p>{{ screen }}</p>
            </div>
        </div>
        <div class="calculatorButtonsContainer">
            <form id="calculatorButtons">
                <button id="clearBtn" @click.prevent="screen = ``">CLEAR</button>
                <button id="deleteBtn" @click.prevent="deleteLastNumber()">DELETE</button>
                <button @click.prevent="addNumber(7)">7</button>
                <button @click.prevent="addNumber(8)">8</button>
                <button @click.prevent="addNumber(9)">9</button>
                <button @click.prevent="opUsed(`/`)">÷</button>
                <button @click.prevent="addNumber(4)">4</button>
                <button @click.prevent="addNumber(5)">5</button>
                <button @click.prevent="addNumber(6)">6</button>
                <button @click.prevent="opUsed(`x`)">x</button>
                <button @click.prevent="addNumber(1)">1</button>
                <button @click.prevent="addNumber(2)">2</button>
                <button @click.prevent="addNumber(3)">3</button>
                <button @click.prevent="opUsed(`-`)">-</button>
                <button @click.prevent="addNumber(`.`)">.</button>
                <button @click.prevent="addNumber(0)">0</button>
                <button @click.prevent="equation()">=</button>
                <button @click.prevent="opUsed(`+`)">+</button>
            </form>
        </div>
    </main>
</template>

<style scoped>
.calculatorContainer{
    display: flex;
    flex-direction: column;
    background-color: grey;
    border: 2px solid black;
    border-radius: 7px;
    height: 500px;
    width: 400px;
    padding: 12px;
}
.calculatorScreenContainer{
    display: flex;
    align-self: center;
}
#calculatorScreen{
    display: flex;
    justify-content: flex-end;
    align-items: center;
    height: 100px;
    width: 300px;
    background-color: rgb(236, 236, 236);
    border-radius: 7px;
    border: 2px solid black;
    margin-top: 10px;
    font-size: 220%;
    padding: 2%;
}
.calculatorButtonsContainer{
    display: flex;
    margin: auto;
    flex-wrap: wrap;
}
#calculatorButtons{
    display: grid;
    gap: 5px;
    height: 330px;
    width: 330px;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(5, 1fr);
}
button{
    background-color: rgb(236, 236, 236);
    border-radius: 5px;
    font-size: large;
}
#clearBtn{
    grid-area: 1/1/2/3;
    background-color: rgba(255, 0, 0, 0.253);
}
#deleteBtn{
    grid-area: 1/3/2/5;
    background-color: rgba(0, 0, 255, 0.349);
}
</style>