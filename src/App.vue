<script setup>
  import { Alert } from 'bootstrap';
  import { reactive } from 'vue';
  import Form from './components/Form.vue'

  const state = reactive({
    inputValue1: '',
    inputValue2: '',
    operators: '',
    result: '',
  });

  const addition = (x, y) => x + y;
  const subtraction = (x, y) => x - y;
  const multiplication = (x, y) => x * y;
  const division = (x, y) => x && y !== 0 ? x / y : "Não é possível dividir um número por zero.";

  const calculateResult = () => {
    if (!isNaN(state.inputValue1) && !isNaN(state.inputValue2)) {
      let x = parseFloat(state.inputValue1);
      let y = parseFloat(state.inputValue2);

      const { operators } = state;

      switch (operators) {
        case "addition":
          return addition(x, y);
        case "subtraction":
          return subtraction(x, y);
        case "multiplication":
          return multiplication(x, y);
        case "division":
          return division(x, y);
        default:
          return "Escolha uma operação aritmética para obter um resultado";
      }
    } else {
      alert("Erro: Os valores adicionados não são números");
    }  
  };

  const showResults = () => {
    state.result = calculateResult();
    return state.result;
  };


</script>

<template>
  <div class="container">    
    <Form :input1-value="state.inputValue1" :input2-value="state.inputValue2" :operators="state.operators" 
      :input1 ="event => state.inputValue1 = event.target.value"
      :input2="event => state.inputValue2 = event.target.value"
      :change-operators="event => state.operators = event.target.value"
      :show-results="showResults()"
    ></Form>
  </div>
</template>

<style scoped>

</style>
