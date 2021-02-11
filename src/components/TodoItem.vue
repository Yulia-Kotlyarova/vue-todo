<template>
    <div class = "todo-item">
        <p v-bind:class="{'completed': todo.completed}"> 
            <input type="checkbox" 
            v-on:change="onMarkToggle"
            v-bind:checked="todo.completed"
            >
            {{ todo.title }} </p>  
        <button @click="$emit('del-todo', todo.id)" class = "delete-btn"> delete </button>
    </div>
</template>

<script>
    export default {
        name: "TodoItem",
        props: ["todo"],
        methods: {
            onMarkToggle() {
                this.todo.completed = !this.todo.completed;
            }
        }
    }
</script>

<style scoped>
    .todo-item {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 20px 10px;
        margin: 10px 0;
        border: 1px solid rgb(28, 170, 163);
        border-radius: 3px;
    }

    .completed {
        text-decoration: line-through;
        color: #727d88;
    }

    .delete-btn {
        border: none;
        outline: none;
        border-radius: 3px;
        padding: 5px 7px;
    }
</style>