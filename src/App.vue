<template>
  <div class="container">
    <h1>Calculadora Aritmética</h1>
    <div class="form-group">
      <label for="numero1" class="numero-label">Número 1:</label>
      <input v-model.number="numero1" id="numero1" type="number" class="form-control" />
    </div>
    <div class="form-group">
      <label for="numero2" class="numero-label">Número 2:</label>
      <input v-model.number="numero2" id="numero2" type="number" class="form-control" />
    </div>
    <div class="form-group">
      <label for="operacao">Operação:</label>
      <select v-model="operacao" id="operacao" class="form-control">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
    </div>
    <div class="form-group">
      <label>Resultado:</label>
      <p :class="{ erro: resultado === 'Erro: Divisão por zero' }">{{ resultado }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

// Definindo os estados reativos
const numero1 = ref(0);
const numero2 = ref(0);
const operacao = ref('+');

// Propriedade computada para calcular o resultado
const resultado = computed(() => {
  switch (operacao.value) {
    case '+':
      return numero1.value + numero2.value;
    case '-':
      return numero1.value - numero2.value;
    case '*':
      return numero1.value * numero2.value;
    case '/':
      return numero2.value !== 0 ? numero1.value / numero2.value : 'Erro: Divisão por zero';
    default:
      return 0;
  }
});
</script>

<style scoped>
.container {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 2px 2px 12px rgba(0, 0, 0, 0.1);
  background-color: #f9f9f9;
}

h1 {
  color: #333;
  font-size: 1.8em;
  margin-bottom: 20px;
  text-align: center;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

input, select {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 1em;
}

p {
  margin-top: 10px;
  font-weight: bold;
  font-size: 1.2em;
}

.erro {
  color: red;
}

.numero-label {
  color: rgb(104, 230, 31);
}
</style>
