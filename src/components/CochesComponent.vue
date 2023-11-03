<template>
  <div>
    <h1>Coches Component</h1>
    <div v-for="car in coches" :key="car">
        <h1 style="color:blue">
            {{car.marca}} , {{car.modelo}}
        </h1>
        <h2 style="color:red">
            Conductor: {{car.conductor}}
        </h2>
        <img :src="car.imagen" style="width:150px; height:150px"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Global from './Global'
//SI NECESITO VARIABLES QUE SEAN DECLARADAS PARA TODOS 
//LOS METODOS QUE TENGAMOS EN EL COMPONENT, LO HAREMOS AQUI
var urApiCoches= Global.urlApiCoches;
export default {
    name:"CochesComponent",
    data(){
        return{
            coches:[]
        }
    },
    mounted(){
        var request= "/webresources/coches";
        axios.get(urApiCoches + request).then((response)=>{
            this.coches=response.data;
        })
    }
}
</script>

<style>

</style>