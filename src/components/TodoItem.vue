<template>
    <div class="todo-item">
        {{ props.todoItem.title }} {{ props.todoItem.id }}
    </div>
    <button @click="handleDelete(props.todoItem.id)"> deleteItem</button>
</template>

<script setup>
import { defineEmits, defineProps } from 'vue'

const emit = defineEmits(['delete-todo-item'])

const props = defineProps({
    todoItem: {
        type: Object,
        required: true,
    }
})

function handleDelete(id) {
    emit('delete-todo-item', id)
}
</script>

<style scoped>
.todo-item{
    margin: 8px 0;
    padding: 9px 30px;
    border-radius: 15px;
    background-color: black;
    color: aliceblue;
}
</style>