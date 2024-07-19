<template>
    <div class="task" :class="stateClass">
        <p>{{ task.nome }}</p>
    </div>
</template>

<script>
    export default{
        props:{
            task:{type: Object, required: true}
        },
        computed:{
            stateClass(){
                return{
                    pending: this.task.pending,
                    done: !this.task.pending
                }
            }
        }
    }
</script>

<style>
    .task{
        box-sizing: 250px;
        width: 200px;
        padding: 15px;
        margin: 5px;
        text-align: center;
        font-weight: 500;
        cursor: pointer;
        user-select: none;
        border-top-left-radius: 10px;
        border-top-right-radius: 10px;
    }

    .pending{
        border-top: 5px solid #800000;
        background-color: #B22222;
    }

    .done{
        border-top: 5px solid #ADD8E6			;
        background-color: #4682B4;
        text-decoration: line-through;
    }
</style>