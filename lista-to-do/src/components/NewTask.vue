<template>
    <div class="new-task">
        <input class="form-element" v-model="name" @keydown.enter="add" type="text" placeholder="Nova tarefa?">
        <button class="form-element" @click="add">+</button>
    </div>
</template>

<script>
    export default{
        data(){
            return {
                name:''
            }
        },
        methods:{
            add(){
                this.$emit('taskAdded', {name: this.name})
                this.name = ''
            }
        }
    }
</script>

<style>
    .new-task{
        margin-bottom: 15px;
    }
    .form-element{
        outline: none;
        font-size: 20px;
    }

</style>