<template>
  <div id="app" class="container">
    <h1 class="text-center"> zi._.u </h1>
    
    <AddTodoItem @add-Todo="addTodo"/>
    <hr>
 
  <TodoList :todos="todos"
        @toggle-Checkbox="toggleCheckbox"
        @delete-item="deleteItem"
  />

  </div>

</template>
<script>
import TodoList from '@/components/TodoList'
import AddTodoItem from '@/components/AddTodoItem'
export default {
  components:{
    TodoList,
    AddTodoItem
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