<script setup>
import { reactive } from 'vue';

const estado = reactive({
  numero1: 0,
  numero2: 0,
  operacao: '+',
  resultado: 0
});

const calcular = () => {
  const { operacao } = estado;
  switch (operacao) {
    case '+':
      return estado.resultado = parseInt(estado.numero1) + parseInt(estado.numero2);
    case '-':
      return estado.resultado = parseInt(estado.numero1) - parseInt(estado.numero2);
    case '*':
      return estado.resultado = parseInt(estado.numero1) * parseInt(estado.numero2);
    case '/':
      return estado.resultado = parseInt(estado.numero1) / parseInt(estado.numero2);
    default:
      return estado.resultado = 0;
  }
}
</script>

<template>
  <div id="app" class="container">
    <div class="row text-center">
      <h1 class="center">Calculadora aritimética</h1>
    </div>
    <div class="row mt-4">
      <div class="col-5">
        <input class="form-control" type="number" @keyup="evento => estado.numero1 = evento.target.value">
      </div>
      <div class="col-2">
        <select class="form-control" @change="evento => estado.operacao = evento.target.value">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
        </select>
      </div>
      <div class="col-5">
        <input class="form-control" type="number" @keyup="evento => estado.numero2 = evento.target.value">
      </div>
    </div>
    <div class="row">
      <button class="btn - btn-primary mt-4"
        @click="calcular(estado.numero1, estado.operacao, estado.numero2)">Calcular</button>
    </div>
    <div class="row text-bg-light text-center mt-4">
      <h3>Resultado: {{ estado.resultado }}</h3>
    </div>
  </div>
</template>

<style scoped></style>
