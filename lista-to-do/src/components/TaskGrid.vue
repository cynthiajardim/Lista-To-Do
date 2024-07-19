<template>
    <div class="task-grid">
        <template v-if="tasks.length">
            <UniqueTask v-for="task in tasks" :key="task.nome" :task="task"></UniqueTask>
        </template>
        <p v-else>Nenhuma tarefa :)</p>
    </div>
</template>

<script> 
    import UniqueTask from './UniqueTask.vue';

    export default{
        components: {UniqueTask},
        props:{
            tasks: {type: Array, required: true}
        }
    }
</script>


<style>
    .task-grid{
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>
