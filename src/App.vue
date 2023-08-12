<script setup>
import { reactive  } from 'vue';

const estado = reactive({
  filtro:'+',
  valor1: ' ',
  valor2: ' ',
})
const calcularSoma = () =>{
  let n1 = parseFloat(estado.valor1)
  let n2 = parseFloat(estado.valor2)
  return  n1 + n2 
}
function limpar(){
  estado.valor1=""; 
  estado.valor2="";
}

const calcularSub = () =>{
  let n1 = parseFloat(estado.valor1)
  let n2 = parseFloat(estado.valor2)
  return  n1 - n2
}
const calcularDiv = () =>{
  let n1 = parseFloat(estado.valor1)
  let n2 = parseFloat(estado.valor2)
  return  n1 / n2
}
const calcularMUl = () =>{
  let n1 = parseFloat(estado.valor1)
  let n2 = parseFloat(estado.valor2)
  return  n1 * n2
}
const calculoDosValores= ()=>{
const { filtro} = estado;
switch (filtro) {
  case '+':
    return calcularSoma()  ;
    case '-':
    return calcularSub();
    case '/':
    return  calcularDiv() ;
    case '*': 
    return calcularMUl();
  default:
    return '0' ;
}

}
function resultado() {
  const valorCalculado = calculoDosValores();

  if (isNaN(valorCalculado)) {
    return 'Resultado ';
  } else {
    return valorCalculado;
  }
}
</script>
<template>
  <div class="container ">
    <div class="row mt-4">
      <div class="col-12 text-center">
        <h1 class="fs-2">Calculadora Artimétrica</h1>
      </div>
    </div>
    <form alin="center">
      <div class="row mt-4.5"  >
        <div class="col-5 " >
          <input :value="estado.valor1" @keyup="evento => estado.valor1= evento.target.value" class="form-control w-30" type="number" required placeholder="Digite o numero: ">
        </div>
        <div class="col-md-2 ">
            <select @change="evento => estado.filtro= evento.target.value" class="form-control ">
              <option value="+">+</option>
              <option value="-">-</option>
              <option value="/">/</option>
              <option value="*">*</option>
            </select>
        </div>
        <div class="col-4 ms-4.5 ">
          <input :value="estado.valor2" @keyup="evento => estado.valor2= evento.target.value" class="form-control" type="number" required placeholder="Digite o numero: ">
        </div>
      </div>
      <div class="row">
        <div class="col-6.5  mt-2">
          <p class="r rounded p-2 ">{{ resultado() }}</p>
        </div>
        <div class="col-2 ">
          <button  class=" mt-2 rounded" @click.prevent="limpar()">Limpar</button>
        </div>
      </div>

    </form>
  </div>
</template>
  
<style scoped>
.container{
  width: 400px;
  height: 400px;
  background-color: cadetblue;
}
.r{
background-color: white;
}
.row{
  display: flex;
  justify-content: center;
}
select{
  cursor: pointer;
}

</style>
