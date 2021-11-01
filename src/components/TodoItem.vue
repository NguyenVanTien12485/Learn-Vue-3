<template>
  <p :class="['list-todo_item', todoProps.isCompleted ? 'is-completed' : '']">
      <input type="checkbox" :checked="todoProps.isCompleted" @change="changeCompleted">
      {{ todoProps.title }}
      <button class="del-btn" @click="deleteItem">Delete</button>
  </p>
</template>

<script>
// import {ref} from 'vue'
export default {
    name: 'TodoItem',
    props: ['todoProps'],
    setup(props, context) {
        const changeCompleted = () => {
            context.emit('item-complete', props.todoProps.id)
        }
        const deleteItem = () => {
            context.emit('delete-item', props.todoProps.id)
        }
        return {
            changeCompleted,
            deleteItem
        }
    }
}
</script>

<style>
    .list-todo_item {
        background-color: #f4f4f4;
        padding: 10px;
        border-bottom: solid 1px black;
    
    }
    .del-btn {
        background: red;
        color: white;
        border: none;
        cursor: pointer;
        float: right;
        width: 40px;
        height: 100%;
    }
    .is-completed {
        text-decoration: line-through;
    }
</style>