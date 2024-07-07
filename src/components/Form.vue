<script setup>
    const props = defineProps(['input1', 'input2', 'input1Value', 'input2Value', 'changeOperators', 'operators', 'showResults']);

</script>

<template>
    <form class="form-control p-5 mt-5">
        <div class="row">
            <div class="col-12">
                <h1 class="p-4">Calculadora Aritmética</h1>
            </div>
        </div>
        <div class="row form-group">
            <div class="col-6 mb-3">
                <label class="mb-2 ps-2" for="input1">Digite o primeiro número</label>
                <input required v-model="props.input1Value" @input="props.input1" type="number" class="form-control" id="input1">
            </div>
            <div class="col-6 mb-3">
                <label class="mb-2 ps-2" for="input2">Digite o segundo número</label>
                <input required v-model="props.input2Value"  @input="props.input2"  type="number" class="form-control" id="input2">
            </div>
        </div>
        <div class=" row form-group">
            <div class="col-6">
                <label class="mb-2 ps-2" for="Control-Select">Escolha a operação aritmética</label>
                <select v-model="props.operators" @input="props.changeOperators" class="form-control" id="Control-Select">
                    <option value="addition">Soma</option>
                    <option value="subtraction">Subtração</option>
                    <option value="multiplication">Multiplicação</option>
                    <option value="division">Divisão</option>
                </select>
            </div>
        </div>
        <div class="row">
            <div class="col-12 mt-4 p-3">
                <strong class="h5">Resultado: {{ props.showResults }}</strong>
            </div>
        </div>
    </form>
</template>