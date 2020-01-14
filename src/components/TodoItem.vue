<template>
    <div>
        <b-list-group-item>
            {{ todo.text }}
        </b-list-group-item>
    </div>
</template>

<script>
    export default {
        name: "TodoItem",
        props: ['todo']
    }
</script>

<style scoped>

</style>
