<template>
    <div>
        <form class = "new-todo-form" @submit="onAddTodo" >
            <input class = "new-todo-input" 
                type="text" 
                v-model = "title" 
                name = "title" 
                placeholder="add something">
            <button class = "btn-add" type = "submit"> add </button>
        </form>
    </div>
    
</template>

<script>
    import { v4 as uuidv4 } from 'uuid';
    export default {
        name: "AddTodo",
        data() {
            return {
                title: ''
            }
        },
        methods: {
            onAddTodo(e) {
                e.preventDefault();
                const newTodo = {
                    id: uuidv4(),
                    title: this.title,
                    completed: false
                };
                this.$emit('add-todo', newTodo);
                this.title = '';
            }
        }
    }
</script>

<style scoped>
    .btn-add {
        padding: 10px 20px;
        border: none;
        border-radius: 3px;
        background: rgb(141, 218, 192);
    }
    .new-todo-input {
        padding: 10px 20px;
    }
    .new-todo-form {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

</style>