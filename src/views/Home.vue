<template>
  <h1 class="my-5">Formularios con Vue.js</h1>
  

  <form @submit.prevent="procesarFormulario">
    <Input :tarea="tarea"/>
  </form>
  <hr>
  <!-- <p>
    {{ tarea }}
  </p> -->
  <ListaTareas />
  <div class="inicio">
     
  </div>
  <h1 class="nombre">Brandon Yahir Flores Vazquez
      <br>4°A Tecnologias de la Informacion Desarrollo de Software Multiplataforma
      <br>Aplicaciones Web Orientadas a Servicios
    </h1>
</template>


<script>
import Input from '../components/Input.vue'
import ListaTareas from '../components/ListaTareas.vue'
import {mapActions} from 'vuex'
const shortid = require ('shortid');



export default {
  name: 'Home',
  components: {
    Input, ListaTareas,
  },
  data () {
    return {
      tarea: {
        id: '',
        nombre: '',
        categorias: [],
        estado: '',
        numero: 0,
      }
    }
},
methods: {
    ...mapActions (['setTareas']),
    
    procesarFormulario () {
      console.log(this.tarea)
      if (this.tarea.nombre.trim() === "") {
        console.log('Campo vacio...')
        return
      }
      console.log('No esta vacio...')
      //generar id
      this.tarea.id = shortid.generate()
      console.log(this.tarea.id)
      //enviamos los datos
      this.setTareas(this.tarea)


      this.tarea = {
        id: '',
        nombre: '',
        categorias: [],
        estado: '',
        numero: 0,
      }
    }
  },

}
</script>
<style>

 /* .inicio{
  padding-left:340px; 
  width:450px;
  height:10px;
}  */
.nombre {
  text-align:center;
  font-size: 15px;
  background: green;
  background-size: 50px;
  border-width:2px;
   border-color:#fafaf8;
   border-style: solid dashed ;
   margin: 70px 100px ;
}

</style>
