<template>
    <div>
        <b-card header="TodoList" header-tag="header">
            <template v-slot:footer>
                <b-button variant="success" class="float-right">Add Todo</b-button>
            </template>
        </b-card>
    </div>
</template>

<script>
    export default {
        name: "TodoList"
    }
</script>

<style scoped>

</style>
