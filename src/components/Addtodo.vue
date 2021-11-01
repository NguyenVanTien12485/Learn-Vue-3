<template>
    <form action="" class="form-add" @submit="addItem">
        <input type="text" placeholder="Enter work..."  v-model="title">
        <input type="submit" value="add work" class="add-btn" >
    </form>

</template>

<script>
import {ref} from 'vue'
export default {
    name: 'Addtodo',
    setup(props, context) {
        const title = ref('')
        const addItem = (e) => {
            e.preventDefault()
            const newItem = {
                id: 4,
                title: title.value,
                isCompleted: false
            }
            context.emit('add-todo', newItem)
            title.value= ''
        }
        return {
            title,
            addItem
        }
    }
}
</script>

<style>
    form {
        display: flex;
    }
    input[type='text'] {
        flex: 10;
        padding: 5px;
    }
    input[type='submit']{
        flex: 2;
        background-color: yellow;
    }
</style>