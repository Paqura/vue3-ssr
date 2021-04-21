<template>
    <ul>
        <li :key="todo.id" v-for="todo in todos">{{todo.name}}</li>
        <button @click="addTodo">Add todo</button>
    </ul>
</template>

<script lang="ts">
import { defineComponent, reactive, watchEffect } from 'vue'

export default defineComponent({
    setup() {
        const idGen = (function () {
            let id = 2;

            return () => String(++id)
        })()

        const todos = reactive([{ id: '1', name: 'Foo' }, { id: '2', name: 'Bar' }])
        const addTodo = () => todos.push({ id: idGen(), name: 'hello' })

        watchEffect(() => {
            console.log([...todos])
        })

        return {
            todos,
            addTodo,
        }
    },
})
</script>
