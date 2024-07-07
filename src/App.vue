<script setup>
import { Alert } from 'bootstrap';
import { reactive } from 'vue';

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
          return "Operação inválida";
      }
    } else {
      console.log("Erro: Os valores adicionados não são números");
    }  
  };

  const showResults = () => {
    state.result = calculateResult();
    return state.result
  };
</script>

<template>
  <div class="container">    
    <form class="form-control p-5 mt-5">
      <div class="row">
        <div class="col-12">
          <h1 class="p-4">Calculadora Aritmética</h1>
        </div>
      </div>
      <div class="row form-group">
        <div class="col-6 mb-3">
          <label class="mb-2 ps-2" for="input1">Digite o primeiro número</label>
          <input v-model="state.inputValue1" @input="showResults" type="number" class="form-control" id="input1"></div>
        <div class="col-6 mb-3">
          <label class="mb-2 ps-2"  for="input2">Digite o segundo número</label>
          <input v-model="state.inputValue2" @input="showResults"  type="number" class="form-control" id="input2">
        </div>  
      </div>
      <div class=" row form-group">
        <div class="col-6">
          <label class="mb-2 ps-2"  for="Control-Select">Escolha a operação aritmética</label>
          <select  v-model="state.operators" @change="showResults"  class="form-control" id="Control-Select">
            <option value="addition">Soma</option>
            <option value="subtraction">Subtração</option>
            <option value="multiplication">Multiplicação</option>
            <option value="division">Divisão</option>
          </select>
        </div>
      </div>
      <div class="row">
        <div class="col-12 mt-4 p-3">
          <strong class="h5">Resultado: {{ state.result }}</strong>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>

</style>
