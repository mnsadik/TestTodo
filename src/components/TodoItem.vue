<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete(todo.completed)" v-bind:checked="todo.completed">
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
    export default {
    name: "TodoItem",
    props: ["todo"],
    data(){
        return{
            todos : this.todo
        }
    },
    methods: {
        markComplete(isComplete) {
            this.todos.completed =! isComplete
        }
    }
    }
</script>

<style scoped>
    .todo-item{
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }
    .is-complete{
        text-decoration: line-through;
    }
    .del{
        background: #ff0000;
        color: #fff;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>