<template>
  <div id="app" class="container">
    <h1 class="text-center"> Todo app</h1>
    <input v-model="todoText"
    type="text"
    class="w-100 p-2"
    placeholder="Type todo"
    @keyup.enter="addTodo">
    <hr>
    <Todo
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-checkbox="toggleCheckbox"
      @click-delete="deleteTodo"/>

    
  </div>

</template>
<script>
import Todo from "@/components/ToDo.vue"

export default {
  components:{
    Todo
  }

  
}
</script>