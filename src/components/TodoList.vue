<template>
<ul class="list-group">
 <todo-item 
 v-for="todo in todos" :key="todo.id"
 :todo="todo"
 />
 <li class="list-group-item" v-if="todos.length === 0">No hay elementos</li>
 <todo-footer v-if="todos.length !== 0 " />
 <todo-filtro />
</ul>
</template>

<script>
import { inject,ref,computed,provide } from 'vue'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFiltro from './TodoFiltro.vue'
export default {
  components: { TodoItem, TodoFooter, TodoFiltro },
  setup(){
 
      const todosTodos = inject('todos')

      const estado = ref('all')

      const todos = computed( () => {
          if(estado.value === 'all'){
          return todosTodos.value
          }
          if(estado.value === 'activo'){
              return todosTodos.value.filter(item => item.estado === false)
          }
          if(estado.value === 'completado'){
              return todosTodos.value.filter(item => item.estado === true)
          }
      })

       provide('estado', estado)

      return {todos}
  }

}
</script>

<style>

</style>