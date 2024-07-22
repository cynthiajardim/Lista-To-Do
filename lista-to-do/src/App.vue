<template>
  <div id="app">
   <h1>To Do: </h1>
   <NewTask @taskAdded="addTask"></NewTask>
   <TaskGrid :tasks="tasks" 
   @taskDeleted="removeTask" 
   @stateChange="changeState"></TaskGrid>
  </div>
</template>

<script>
import TaskGrid from './components/TaskGrid.vue';
import NewTask from './components/NewTask.vue';

export default {
  components: { TaskGrid, NewTask },
  data(){
    return{
      tasks:[
        //tarefas para teste
        {nome: 'Iniciar curso', pending: false},
        {nome: 'Arrumar casa', pending: true},
        {nome: 'Estudar para a prova', pending: false}
      ]
    }
  },
  watch: {
    tasks: {
      //verifica profundamente o que foi alterado no objeto observado
      deep: true,
      handler(){
        //converte lista de tasks em string e salva no localStorage
        localStorage.setItem('tasks', JSON.stringify(this.tasks))
      }
    }
  },
  methods:{
    addTask(task){
      const nomeIgual = t => t.nome == task.name
      const naoExiste = this.tasks.filter(nomeIgual).length == 0
      if(naoExiste)
        this.tasks.push({nome: task.name, pending: task.pendig || true})
    },
    removeTask(i){
      this.tasks.splice(i, 1);
    },
    changeState(i){
      this.tasks[i].pending = !this.tasks[i].pending
    }
  },
  created(){
    const tasksString = localStorage.getItem('tasks')
    this.tasks = JSON.parse(tasksString) || []
  }
}
</script>

<style>
  body {
    background-color: #B0C4DE;
  }


</style>
