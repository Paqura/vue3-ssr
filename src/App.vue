<template>
  <div>
    {{count}}
    <p><button @click="increment">Click</button></p>

    <TodoList />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import TodoList from './components/TodoList.vue'


export default defineComponent({
  components: {
    TodoList,
  },

  setup() {
    const count = ref(0);

    const increment = () => count.value++;

    return { count, increment, TodoList }
  },
})
</script>
