<template>
    <div>
        <b-card header="VueDo" header-tag="header">
            <b-list-group>
                <TodoItem v-for="item in list" :todo="item" :key="item.key"/>
            </b-list-group>
            <template v-slot:footer>
                <input type="text" v-model="newTodo" v-on:keyup.enter="addNewTodo()">
                <b-button variant="success" class="float-right" @click="addNewTodo()">Add Todo</b-button>
            </template>
        </b-card>
    </div>
</template>

<script>
    import TodoItem from "./TodoItem";

    export default {
        name: "TodoList",
        components: {TodoItem},
        data() {
            return {
                list: [
                    {
                        id: 1,
                        text: "Put on an ice pack",
                        done: true
                    },
                    {
                        id: 2,
                        text: "1000 stomach crunches",
                        done: true
                    },
                    {
                        id: 3,
                        text: "Use a deep pore cleanser lotion",
                        done: true
                    },
                    {
                        id: 4,
                        text: "Use a water activated gel cleanser",
                        done: true
                    },
                    {
                        id: 5,
                        text: "Use a honey almond body scrub with an exfoliating gel scrub",
                        done: true
                    },
                    {
                        id: 6,
                        text: "Apply an herb mint facial mask, leave on for 10 minutes",
                        done: true
                    },
                    {
                        id: 7,
                        text: "Use an aftershave lotion with little or no alcohol",
                        done: true
                    }
                ],
                newTodo: ""
            }
        },
        methods: {
            addNewTodo() {
                if(!this.newTodo) {
                    alert("Please enter todo text.");
                    return
                }

                const newId = Math.max.apply(null, this.list.map(t => t.id)) + 1;

                this.list.push({
                    id: newId,
                    text: this.newTodo,
                    done: false
                })

                this.newTodo = "";
            }
        }
    }
</script>

<style scoped>

</style>
