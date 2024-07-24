<template>
    <div class="task-grid">
        <template v-if="tasks.length">
            <UniqueTask v-for="(task, i) in tasks" 
            :key="task.nome" 
            :task="task"
            @taskDeleted="$emit('taskDeleted', i)"
            @stateChange="$emit('stateChange', i)"></UniqueTask>
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
        flex-direction: column;
    }
</style>
