<template>
  <div id="app" class="container">
    <h1 class="text-center"> zi._.u </h1>
    <input 
      v-model="todoText"
      type="text"
      class="w-100 p-2"
      placeholder="INSERT TEXT"
      @keyup.enter="addTodo">
    <hr>
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
  data(){
    return{
      todoText:'',
      todos:[
        {id : 1, text: "buy a car", checked : false },
        {id : 2, text: "buy a house", checked : true },
        {id : 3, text: "buy a phone", checked : false }
      ]
    }
  },
  methods:{
    addTodo(e){
      this.todos.push({
        id : Math.random(),
        text : e.target.value,
        checked : false,
        })
        this.todoText=''
    },
    toggleCheckbox({id, checked}){
      const index = this.todos.findIndex(todo =>{
        return todo.id ===id;
      });
      this.todos[index].checked = checked;
    },
    deleteItem(id){
    //   const index = this.todos.findIndex(todo =>{
    //     return todo.id === id;
    //   })
    // this.toods.splice(index, 1);

    this.todos = this.todos.filter(todo=> todo.id !== id);

    }
  }
}
</script>