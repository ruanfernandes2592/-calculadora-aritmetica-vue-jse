<script setup>
import { reactive } from 'vue';

const numeros = reactive({
  n1: 0,
  n2: 0,
  operacao: 'somar',
  resultado: 0,
});

function calcular() {
  if(numeros.operacao === 'somar') {
    numeros.resultado = numeros.n1 + numeros.n2
  } else if(numeros.operacao === 'subtrair'){
    numeros.resultado = numeros.n1 - numeros.n2
  } else if(numeros.operacao === 'dividir'){
    numeros.resultado = numeros.n1 / numeros.n2
  } else if(numeros.operacao === 'multiplicar'){
    numeros.resultado = numeros.n1 * numeros.n2
  }
}

function escolha(op, e){
  if(op === "inputN1"){
    if(e.target.value === ''){
      numeros.n1 = 0
    } else {
      numeros.n1 = Number(e.target.value)
    }
    calcular()
  } else if(op === "inputN2"){
    if(e.target.value === ''){
      numeros.n2 = 0
    } else {
      numeros.n2 = Number(e.target.value)
    }
    calcular()
  }else if(op === "operador"){
    numeros.operacao = e.target.value
    calcular()
  }
}

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 rounded-3 d-flex justify-content-center text-bg-secondary">
      <h1>Calculadora Aritmética</h1>
    </header>
    <form>
      <div class="row">
        <div class="col">
          <input type="number"  @keyup="(e) => escolha('inputN1', e)" placeholder="Digite um número" class="form-control text-bg-light m-1">
          <select class="form-select text-bg-light m-1" @change="(e) => escolha('operador', e)">
            <option value="somar">+ Somar</option>
            <option value="subtrair">- Subtrair</option>
            <option value="dividir">/ Dividir</option>
            <option value="multiplicar">* Multiplicar</option>
          </select>
          <input type="number" @keyup="(e) => escolha('inputN2', e)" placeholder="Digite um número" class="form-control text-bg-light m-1">
        </div>
        <div class="col form-control d-flex justify-content-center pt-4 text-bg-light m-1">
          {{ numeros.resultado }}
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>

</style>
