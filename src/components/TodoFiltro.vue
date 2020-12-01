<template>
<div class="card mt-3 ">
    <div class="card-body d-flex justify-content-between aling-item-center">
   <span role="button" @click="filtrar('activo')">
     Activos
   </span>
     <span role="button" @click="filtrar('all')">
     Todos
   </span>
     <span role="button" @click="filtrar('completado')">
     Completos
   </span>
    </div>
</div>
</template>

<script>
import { inject } from 'vue'
export default {

    setup(){

        const estado = inject('estado')

        const filtrar = str =>{
            estado.value = str
        }

        return {filtrar}


    }

}
</script>

<style>

</style>