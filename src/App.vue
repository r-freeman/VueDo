<template>
    <div id="app">
        <b-container class="my-5">
            <b-row>
                <b-col>
                    <TodoList/>
                </b-col>
            </b-row>
        </b-container>
    </div>
</template>

<script>
    import TodoList from "./components/TodoList";

    export default {
        name: 'app',
        components: {TodoList}
    }
</script>

<style>

</style>
