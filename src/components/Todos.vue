<template>
    <div class = "todos-wrapper">
        <h1> Do it well </h1>
        <div v-bind:key = "todo.title.split(' ').join()" v-for = "todo in todos">
            <TodoItem 
            v-bind:todo = "todo"
            v-on:del-todo="$emit('del-todo', todo.id)"
            />
        </div>
    </div>
</template>

<script>
    import TodoItem from './TodoItem.vue';

    export default {
        name: "Todos",
        components: {
            TodoItem,
        },
        props: ["todos"]
    }
</script>

<style scoped>
    .todos-wrapper {
        max-width: 500px;
        min-width: 300px;
        margin: 0 auto;
    }

</style>