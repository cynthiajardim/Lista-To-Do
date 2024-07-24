<template>
    <div class="new-task">
        <input class="form-element" v-model="name" @keydown.enter="add" type="text">
        <button class="form-element form-element-btn" @click="add">+</button>
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
    .form-element-btn{
        color: #fff;
        width: 30px;
        height: 30px;
        border-radius: 50px;
        border-color: #000;
        background-color: #000;
        border-style: none;
    }
    input[type="text"]{
        background-color: #B2A8A8;
        border-style: none;
    }

</style>