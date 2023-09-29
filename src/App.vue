<script setup>
import { reactive } from 'vue';

const digitos = reactive({
  digitoA: 0,
  digitoB: 0
})


function multiplicacao(){
  return digitos.digitoA * digitos.digitoB
}
function soma(){
  return digitos.digitoA + digitos.digitoB
}
function divisao(){
  return digitos.digitoA / digitos.digitoB
}

const estado = reactive({
  filtro: 'multiplicar',
  resultado: 0
})

function atualizarResultado(){
  switch (estado.filtro){
      case 'multiplicar':
        return estado.resultado = multiplicacao();
      case 'somar':
        return estado.resultado = soma()
      case 'dividir':
        return estado.resultado = divisao()
    }

}
</script>

<template>
  <input v-model.number="digitos.digitoA" @input="atualizarResultado" type="number" placeholder="Digite o primeiro valor">
  <input v-model.number="digitos.digitoB" @input="atualizarResultado" type="number" placeholder="Digite o segundo valor">
  <span>{{ estado.resultado }}</span>

  <select v-model="estado.filtro" @change="atualizarResultado" class="form-control">
      <option value="multiplicar">Multiplicação</option>
      <option value="somar">Soma</option>
      <option value="dividir">Divisão</option>
  </select>
</template>

<style scoped>

</style>
