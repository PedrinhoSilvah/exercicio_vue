<script setup>
import { reactive } from 'vue';


  const operacao = reactive({
    input1: 0,
    input2: 0,
    filtro: '+',
  })



  const resultado = () => {
    const {input1, input2, filtro,} = operacao;

    const num1 = parseFloat(input1);
    const num2 = parseFloat(input2);

    switch(filtro){
      case '+' :
        return num1 + num2
      case '-':
        return num1 - num2;
      case '÷':
        return num1 / num2;
      case 'x':
        return num1 * num2;
      default:
        return 'testando'
    }
  }


  
</script>

<template>

  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>Calculadora</h1>
    </header>
    <div class="calculo">
      <input  @keyup="evento => operacao.input1 = evento.target.value" class="mb-4 mt-4 rib" required type="number">
      <div class="col-md-2">
        <select @change="evento => operacao.filtro = evento.target.value" class="form-control">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="÷">÷</option>
          <option value="x">x</option>
        </select>
      </div>
      <input  @keyup="evento => operacao.input2 = evento.target.value" class="mb-4 mt-4 rib" requi type="number">
      <div @keyup="resultado" class="resultado">
         O Resultado foi: {{ resultado() }}
      </div>
    </div>
  </div>

</template>

<style scoped>
.form-control {
  text-align: center;
}
.rib{
  text-align: center;
}
</style>
