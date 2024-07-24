<template>
  <div id="app">
    <div class="init">
        <h1>To Do</h1>
        <h2>{{dataHoje}}</h2>
        <NewTask @taskAdded="addTask"></NewTask>
    </div>
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
      ],
      dataHoje:(new Date()).getDate()+'/'+((new Date()).getMonth()+1)
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
    background: linear-gradient(0.90turn, #ffde59, #ff914d);  
  }

  .init{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .init h1{
    color: #ffd200;
    text-shadow: -15px 5px 20px #ced0d3;
    text-shadow: 5px 5px 0px #FF7154, 
    10px 10px 0px #FF9253;
    font-family: "Vampiro One", system-ui;
    font-weight: 400;
    font-style: normal;
    font-size: 134px;
    margin: 0;
  }

  .init h2{
    font-family: "BioRhyme Expanded", serif;
    font-weight: 700;
    font-style: normal;
    font-size: 30px;
    margin:0;
  }

</style>
