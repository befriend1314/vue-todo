<template>
    <section class="real-app">
        <input type="text" class="add-input" autofocus placeholder="接下来要做什么" @keyup.enter="addTodo">
        <Item :todo="todo" v-for="todo in filterTodos" :key="todo.id" @del="deleteTodo"></Item>
        <Tabs :filter="filter" :todos="todos" @toggle="toggleFilter" @clearAllcompleted="clearAllcompleted"></Tabs>
    </section>
</template>
<script>
import Item from './item.vue'
import Tabs from './tabs.vue'
let id = 0
export default {
    data() {
        return {
            todos: [],
            filter: 'all'
        }
    },
    computed: {
        filterTodos() {
            if( this.filter === 'all') return this.todos
            const completed = this.filter === 'completed'
            return this.todos.filter(todo => completed === todo.completed)
        }
    },
    methods: {
        addTodo(e) {
            if( e.target.value.trim() === "") return false
            this.todos.unshift({
                id: id++,
                content: e.target.value.trim(),
                completed: false
            })
            e.target.value = ''
        },
        deleteTodo(id) {
            this.todos.splice(this.todos.findIndex(todo => todo.id === id), 1)
        },
        toggleFilter(state) {
            this.filter = state
        },
        clearAllcompleted() {
            this.todos = this.todos.filter(todo => !todo.completed )
        }
    },
    components: {
        Item,
        Tabs
    }
}
</script>

<style lang="less" scoped>
.real-app{
    width: 600px;
    margin: 0 auto;
    box-shadow: 0 0 5px #666;
}
.add-input{
    position: relative;
    margin: 0;
    width: 100%;
    font-size: 12px;
    line-height: 1.4em;
    border: none;
    outline: none;
    box-sizing: border-box;
    font-smoothing: antialiased;
    padding: 16px 16px 16px 36px;
    box-shadow: inset 0 -2px 1px rgba(0, 0, 0, 0.03);
}

</style>