<template>
    <div class="task" :class="stateClass" @click="$emit('stateChange', task)">
        <!-- click.stop para o evento para que ele não propague o evento para a emissão da mudança de estado, do contrário teremos um problema -->
        <span class="close" @click.stop="$emit('taskDeleted', task)">x</span>
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
        position: relative;
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
        border-top: 5px solid #83d7f3;
        background-color: #4682B4;
        text-decoration: line-through;
    }

    .pending .close{
        background-color: #ae0404;
    }

    .done .close{
        background-color: #a5c7e3;
    }

    .close{
        position: absolute;
        right: 10px;
        top: 10px;
        border-radius: 10px;
        font-size: 0.9rem;
        font-weight: 600;
        height: 20px;
        width: 20px;
        display: flex;
        justify-content: center;
    }
</style>