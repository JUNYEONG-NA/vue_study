<template>
     <div>
     <Todo
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-Checkbox="toggleCheckbox"
      @delete-item="deleteItem"
      />
     </div>
</template>

<script>

import Todo from "@/components/ToDo"

export default {
    components:{
        Todo
    },
    props :{
        todos:{
            type : Array,
            required : true
        }
    },
    methods:{
        toggleCheckbox(value){
                this.$emit('toggle-Checkbox', value)
        },
        deleteItem(todoId){
            this.$emit("delete-item", todoId)
        }
    }
}
</script>

<style>

</style>