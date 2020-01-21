<template>
    <div>
        <b-card header="VueDo" header-tag="header">
            <b-list-group>
                <TodoItem
                        v-on:complete-todo="completeTodo"
                        v-on:undo-todo="undoTodo"
                        v-on:delete-todo="deleteTodo"
                        v-for="item in list" :todo="item" :key="item.key"/>
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
                        done: false
                    },
                    {
                        id: 2,
                        text: "1000 stomach crunches",
                        done: false
                    },
                    {
                        id: 3,
                        text: "Deep pore cleanser lotion",
                        done: false
                    },
                    {
                        id: 4,
                        text: "Water activated gel cleanser",
                        done: false
                    },
                    {
                        id: 5,
                        text: "Honey almond body scrub with an exfoliating gel scrub",
                        done: false
                    },
                    {
                        id: 6,
                        text: "Apply an herb mint facial mask, leave on for 10 minutes",
                        done: false
                    },
                    {
                        id: 7,
                        text: "Aftershave lotion with little or no alcohol",
                        done: false
                    },
                    {
                        id: 8,
                        text: "Then moisturizer, then an anti-aging eye balm",
                        done: false
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
                });

                this.newTodo = "";
            },
            completeTodo(todo) {
                const todoIndex = this.list.indexOf(todo);
                this.list[todoIndex].done = true;
            },
            undoTodo(todo) {
                const todoIndex = this.list.indexOf(todo);
                this.list[todoIndex].done = false;
            },
            deleteTodo(todo) {
                const todoIndex = this.list.indexOf(todo);
                this.$delete(this.list, todoIndex)
            }
        }
    }
</script>

<style scoped>

</style>
