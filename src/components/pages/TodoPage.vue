<template>
    <div class="todo-list">
      <TodoInput @create-new-item="handleItemAdd" />
      <TodoItem
       v-for="(todoItem, index) in todoes"
            :key="index"
            :todo-item="todoItem"
            @delete-todo-item="handleTodoItemDelete"
        />
    </div>
    <div>
        <h2>Удалённые todoItem</h2>
        <TodoItem
       v-for="(todoItem, index) in deleteTodoes"
            :key="index"
            :todo-item="todoItem"
            @delete-todo-item="handleTodoItemDelete"
        />
    </div>

</template>

<script setup>
import { ref } from 'vue'
import TodoItem from '../TodoItem.vue'
import TodoInput from '../TodoInput.vue'

const todoes = ref([])
const deleteTodoes = ref([])

function handleItemAdd(todoTitle) {
    todoes.value.push({
        id: todoes.value.length + deleteTodoes.value.length+ 1,
        title: todoTitle,
    })
} 

function handleTodoItemDelete(id) {
    const index = todoes.value.findIndex((todoItem) => todoItem.id === id)

    if ( !!index) {
        const deletedItem = todoes.value.splice(index, 1)
        deleteTodoes.value.push(deletedItem)
    }
}
</script>

<style scoped>
.todo-list {
    display: flex;
    flex-direction: column;
    max-width: 450px;
    margin-right: 100px;
}
</style>