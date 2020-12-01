<template>
  
  <form @submit.prevent="agregarTarea">
      <input 
           type="text"
           class="form-control my-3"
           placeholder="Ingrese nueva tarea"
           v-model.trim="texto"
      >
  </form>
</template>

<script>
import { inject, ref } from 'vue'
export default {

    setup(){

     const todos = inject('todos') // toma la key que pusimos en el componente padre y accedemos a los valores
                                    // Es reactivo, todo lo que modificamos acá se modifica en el array original
     const texto = ref('')
     const agregarTarea = () =>{
         if(texto.value === ''){
             console.log("Esta vacio");
             return 
         }
         const todo = {
             texto: texto.value,
             estado: false,
             id: Date.now()
         }
        todos.value.push(todo)
     
        texto.value = ''

     }

     return { agregarTarea, texto } // siempre hay que retornar todo

    }

}
</script>

<style>

</style>