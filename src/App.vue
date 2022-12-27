<script setup>
import {ref, computed} from 'vue'

const listado = ref([]);

const cantidadTareas = ref(0);

const agregar = () => {
  const tarea = document.getElementById('tarea').value
  if(tarea != ''){
    //console.log(tarea)
    listado.value.push(tarea)
    cantidadTareas.value++
  }
  //para sacar el texto del campo
  const tareaAux = document.getElementById('tarea').value = ''
};

const limpiar = () => {
  listado.value = [] 
  tareasFin.value = 0
  cantidadTareas.value = 0
};

const borrar = (indice) => {
    //si el indice es igual a 0, elimino con
  if(indice == 0){
    listado.value.splice(0, 1)
  }
  //cuendo es indice igual al largo de la lista, elimino con pop():
  else if(listado.value.length-1 == indice){
    listado.value.pop()
  }
  //si no eliminao asi, esta entre medio
  else{
    listado.value.splice(indice, 1)
  }
};

const tareasFin = ref(0);

const contarTareasFin = () => {
  tareasFin.value++
};

const item = "item.png"

</script>

<template>
  <body>

    <header class="container">
    <h1 class="titulo">To Do List</h1>
    </header>
  
    <main class="container">
      <section class="containerbis">
        <input id="tarea" type="text">
        <button class="btn-principal" id="agregar" @click="agregar">Agregar a lista</button>
      </section>
      <!--<h2>{{listado}}</h2>-->
      <!--<h3>Listado</h3>-->
      <h3 id="listado" v-for="(tarea, index) in listado" :key="index"> <img id="item" :src="item"> {{ tarea }} <button class="btn-principal" id="listo" @click="borrar(index), contarTareasFin()">listo</button> <button class="btn-principal" id="borrar" @click="borrar(index)">borrar</button></h3>
      <h5 id="contador">Tareas Completadas: {{ tareasFin }} / {{ cantidadTareas }}</h5>
      <button id="btn-limpiar" class="btn-principal" @click="limpiar">Limpiar</button>
    </main>

  </body>
 
</template>

<style>
@font-face {
    font-family: "MADE_Evolve_Sans_Regular";
    src: url(MADE_Evolve_Sans_Regular.otf);
}

@font-face {
    font-family: "Margin";
    src: url(Margin.otf);
}

@font-face {
    font-family: "Simply_Rounded";
    src: url(Simply_Rounded.ttf);
}


*{
  background-color:rgb(220,208,193);
}

.container{
  display: grid;
  grid-template-columns: 20% 60% 20%;
}

h1{
  grid-column: 2;
  text-align: center;
}

.containerbis{
  grid-column: 2;
  display: grid;
  grid-template-columns: 80% 2% 20%;
  margin-bottom: 40px;
}

.titulo{
  color: #53513a;
  font-family: "Margin";
  letter-spacing: 5px;
  font-size: 450%;
}

#tarea{
  width: 100%;
  height: 100%;
  border-color: #a09688;
  border-style: solid;
  background-color: white;
}

#tarea:focus{
  width: 100%;
  height: 100%;
  border-color: #a09688;
  border-style: solid;
  background-color: rgb(243, 243, 243);
}

#agregar{
  grid-column: 3;
  width: 100%;
  height: 100%;
  margin-top: 3px;
  padding-bottom: 3px;
}

.btn-principal{
  color: black;
  background-color: rgba(118,147,117,255);
  border: none;
  border-radius: 5px;
  font-size: 15px;
  font-family: "Simply_Rounded";
}

.btn-principal:hover{
  background-color: #89a58c;
}

#listado{
  grid-column: 2;
  display: grid;
  grid-template-columns: 10% 75% 10% 2% 10%;
  align-items: center;
  font-size: 30px;
  font-family: "MADE_Evolve_Sans_Regular";
}

#item{
  width: 100%;
  height: 100%;
  grid-column: 1;
}

#listo{
  background-color: #c2d3b7;
  border-radius: 10px;
}

#listo:hover{
  border: 2px ridge #89a58c;
}

#borrar{
  background-color: rgb(187, 151, 151);
  grid-column: 5;
  border-radius: 10px;
}

#borrar:hover{
  border: 2px ridge rgb(173, 134, 134);
}

#contador{
  grid-column: 2;
  font-family: "Simply_Rounded";
  font-size: 15px;
}

#btn-limpiar{
  grid-column: 2;
  width: 20%;
}

</style>