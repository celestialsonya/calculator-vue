
<template>

  <div class="calculator">

    <div class="show">
      <p>{{exp}}</p>
    </div>

    <div class="all-buttons">
      <div class="buttons">
        <button @click="clearExp">ON</button>
        <button>√</button>
        <button>%</button>
        <button @click="calculate">←</button>
      </div>
      <div class="buttons">
        <button @click="(e) => addNumber(e.target.value)" value="7">7</button>
        <button @click="(e) => addNumber(e.target.value)" value="8">8</button>
        <button @click="(e) => addNumber(e.target.value)" value="9">9</button>
        <button @click="(e) => addNumber(e.target.value)" value="/">/</button>
      </div>
      <div class="buttons">
        <button @click="(e) => addNumber(e.target.value)" value="4">4</button>
        <button @click="(e) => addNumber(e.target.value)" value="5">5</button>
        <button @click="(e) => addNumber(e.target.value)" value="6">6</button>
        <button @click="(e) => addNumber(e.target.value)" value="*">×</button>
      </div>
      <div class="buttons">
        <button @click="(e) => addNumber(e.target.value)" value="1">1</button>
        <button @click="(e) => addNumber(e.target.value)" value="2">2</button>
        <button @click="(e) => addNumber(e.target.value)" value="3">3</button>
        <button @click="(e) => addNumber(e.target.value)" value="-">-</button>
      </div>
      <div class="buttons">
        <button @click="(e) => addNumber(e.target.value)" value="0">0</button>
        <button @click="(e) => addNumber(e.target.value)" value=".">.</button>
        <button>=</button>
        <button @click="(e) => addNumber(e.target.value)" value="+">+</button>
      </div>
    </div>

  </div>

</template>

<script>

  import {counter} from "@/counter";

  export default {

    data(){
      return {
        signs: "+-*/",
        exp: ""
      }
    },

    methods: {

      calculate(){

        for (let i = 0; i < this.exp.length; i++){

          const char = this.exp[i]

          for (let j = 0; j < this.signs.length; j++){

            const sign = this.signs[j]

            if (char === sign){

              const num = parseInt(this.exp.slice(0, i))
              const num2 = parseInt(this.exp.slice(i + 1, this.exp.length))
              let result

              switch (sign){
                case "+":
                  result = counter.sum(num, num2)
                  this.exp = result
                  console.log(result)

                  break
                case "-":
                  result = counter.diff(num, num2)
                  this.exp = result
                  console.log(result)

                  break
                case "*":
                  result = counter.multiply(num, num2)
                  this.exp = result
                  console.log(result)

                  break
                case "/":
                  result = counter.div(num, num2)
                  this.exp = result
                  console.log(result)

                  break
              }

            }
          }
        }
      },

      addNumber(number){
        this.exp = this.exp + number
      },
      clearExp(){
        this.exp = ""
      }
    }
  }
</script>

<style>

  @import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

  p{
    font-family: 'Roboto', sans-serif;
    font-size: 25px;
  }

  .calculator{
    margin-top: 5%;
    margin-left: 34%;
    border-radius: 10px;
    padding: 1.5rem;
    width: 23%;
      background-color: rgba(181, 178, 253, 0.75);
  }

  button{
    font-family: 'Roboto', sans-serif;
    font-size: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    border-radius: 10px;
    width: 4rem;
    height: 4rem;
    padding: 1.5rem;
    background-color: rgba(174, 172, 250, 0.98);
    border: none;
  }

  .buttons{
    height: 5rem;
    display: flex;
    justify-content: space-between;
  }

  input{
    border: none;
    padding: 1rem;
    margin: 0 1rem 1rem 1rem;
  }

  .all-buttons{
    display: block;
    align-items: center;
  }

  .show{
    padding: 0 1rem 0 0;
    height: 3rem;
    margin-bottom: 1.5rem;
    background-color: lightcyan;
    display: flex;
    align-items: center;
    justify-content: end;
  }

</style>