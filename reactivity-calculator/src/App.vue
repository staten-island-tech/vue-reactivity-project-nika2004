<template>
  <div id="app">
    <header>
      <h1 class="title">VUE CALCULATOR</h1>
    </header>
    <section class="calculator" id="calculator">
      <calculator></calculator>
    </section>
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  }
 }
</script>

<style>
html{
   font-size:62.5%;  /* =10px */
}
body{
  background-color: #a1c8f7
}
header{
  font-size: 3rem;
  font-family: Georgia, 'Times New Roman', Times, serif
}
header, .calculator {
  margin: 6rem auto;
  text-align: center;
}
.title{
  color: navy
}
.calculator{
  border: 0.8rem solid white;
  width: 40rem;
  height: 48rem;
  background-color: navy;
  font-size: 2rem;
  border-radius: 1rem;
  
}
</style>
