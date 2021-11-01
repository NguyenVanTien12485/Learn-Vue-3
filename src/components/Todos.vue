<template>
  <div>
    <Addtodo @add-todo="addComplete"/>
    <TodoItem 
    v-for="todo in todos" 
    :key="todo.id" 
    :todoProps="todo"
    @item-complete="makeComplete"
    @delete-item="deleteTodo"
    />
  </div>
</template>

<script>
import { ref } from 'vue'
import TodoItem from './TodoItem'
import Addtodo from './Addtodo.vue'
import axios from 'axios'
export default {
    name: 'Todos',
    components: {
        TodoItem,
        Addtodo
    },
    setup() {
        const todos = ref([])
        const getAlltodo = async () => {
            try {
                const res = await axios.get('http://dev.okxe.vn:9002/api/popups')
                todos.value=res.data
            } catch(error) {
                console.log(error)
            }
        }

        getAlltodo()
        const makeComplete = id => {
            todos.value = todos.value.map(todo => {
                if(todo.id === id) todo.isCompleted = !todo.isCompleted;
                return todo
            })
        }
        const deleteTodo = id => {
            todos.value = todos.value.filter(todo => todo.id !== id)
        }
        const addComplete = ACplete => {
            todos.value.push(ACplete)
        }

        return {
            todos,
            makeComplete,
            deleteTodo,
            addComplete,          
        }
    }
}
</script>

<style>

</style>