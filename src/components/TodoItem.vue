<template>
    <div>
        <b-list-group-item class="d-flex justify-content-between align-items-center">
            <span v-if="todo.done" class="done">{{ todo.text}}</span>
            <span v-else>{{ todo.text}}</span>
            <b-button
                v-if="todo.done"
                pill
                variant="outline-danger">&#10005;</b-button>
            <b-button
                v-else
                pill
                variant="outline-success"
                @click="completeTodo(todo)">&#10003;</b-button>
        </b-list-group-item>
    </div>
</template>

<script>
    export default {
        name: "TodoItem",
        props: ['todo'],
        methods: {
            completeTodo(todo) {
                this.$emit("complete-todo", todo);
            }
        }
    }
</script>

<style scoped>
.done{
    text-decoration: line-through;
}
</style>
