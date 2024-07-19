<template>
  <div id="app">
   <h1>To Do: </h1>
   <TaskGrid :tasks="tasks"></TaskGrid>
  </div>
</template>

<script>
import TaskGrid from './components/TaskGrid.vue';

export default {
  components: { TaskGrid },
  data(){
    return{
      tasks:[
        //tarefas para teste
        {nome: 'Iniciar curso', pending: false},
        {nome: 'Arrumar casa', pending: true},
        {nome: 'Estudar para a prova', pending: false}
      ]
    }
  }
}
</script>

<style>
  body {
    background-color: #B0C4DE;
  }


</style>
