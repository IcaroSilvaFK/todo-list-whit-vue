<script setup lang="ts">
import CHeader from './components/CHeader.vue'
import TodoCard from './components/TodoCard.vue'
import CFooter from './components/CFooter.vue'
import { ref } from 'vue'
import { useAutoAnimate } from '@formkit/auto-animate/vue'

const todos = ref([
  {
    title: 'example 1',
    id: window.crypto.randomUUID()
  },
  {
    title: 'example 2',
    id: window.crypto.randomUUID()
  },
  {
    title: 'example 3',
    id: window.crypto.randomUUID()
  }
])
const todo = ref('')
const [parent] = useAutoAnimate()

function add() {
  todos.value.push({
    id: window.crypto.randomUUID(),
    title: todo.value
  })
  todo.value = ''
}

function deleteTodo(todo: string) {
  const filteredTodos = todos.value.filter((t) => t.id !== todo)

  todos.value = filteredTodos
}
</script>

<template>
  <CHeader @create-todo="add" :todo="todo" @change-text="(params) => (todo = params)" />
  <div>
    <ul ref="parent">
      <TodoCard
        v-for="todo in todos"
        :todo="todo.title"
        :key="todo.id"
        :id="todo.id"
        @delete-todo="deleteTodo($event)"
      />
    </ul>
  </div>
  <CFooter>
    <template #footer>
      <span>&copy; Icaro Vieira</span>
    </template>
  </CFooter>
</template>

<style lang="scss" scoped>
div {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 12px;
  max-width: 40%;
  width: 100%;
  margin: 22px auto;
  flex: 1;

  ul {
    width: 100%;
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 12px;
    max-width: 50%;
  }
}
</style>
