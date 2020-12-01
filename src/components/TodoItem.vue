<template>
    <li class="list-group-item d-flex justify-content-between aling-item-center">
        <span role="button" @click="completado(todo.id)" :class="{'tachado': todo.estado}">
         {{todo.texto}}
        </span>
        <span role="button" @click="eliminar(todo.id)">
      <i class="fa fa-times" aria-hidden="true"></i>
        </span>
    </li>
</template>

<script>
import { inject } from 'vue'
export default {
    props:{
        todo:{
            type: Object,
            required: true
        }
    },
    setup(){
 
         const todos = inject('todos')
   
         const eliminar = id =>{
             todos.value = todos.value.filter(item => item.id !== id )
                                                    // cuando item.id sea diferente al id que recibimos
         }
         const completado = id =>{
             todos.value = todos.value.map(item =>{
                 if(item.id === id){
                     item.estado = true
                 }
                 return item // siempre hay que retornarlo
             }) 

         }
         return{eliminar, completado} // todo lo que usemos en la vista se retorna
   }


}
</script>

<style>
.tachado{
    text-decoration: line-through;
}
</style>