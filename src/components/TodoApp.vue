<template>
 <h1>ToDos</h1>
 <todo-form />
 <todo-list />
</template>

<script>
import { provide, ref, watchEffect } from 'vue';
import TodoForm from './TodoForm.vue'
import TodoList from './TodoList.vue';
export default {
  components: { TodoForm, TodoList },
  // al contenedor o al componente principal, hacemos la lista y hacemos que pueda ser accedida por todos los componentes hijos
  setup(){
      // construimos array
      
      const todos =ref([]);

      provide('todos', todos); // Toma 2 parametros, primero la key y después el value para después poder acceder desde los componetnes hijos
      
      if(localStorage.getItem('todos')){
          todos.value = JSON.parse(localStorage.getItem('todos'))
      }
      watchEffect(() =>{
          localStorage.setItem('todos', JSON.stringify(todos.value))
      }) // esta pendiente automaticamente de lo que nosotros le digamos, cada vez que hagamos un cambio del ToDo 
  }

}
</script>

<style>

</style>