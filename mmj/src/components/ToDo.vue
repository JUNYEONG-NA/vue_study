<template>
  <div>
      <div class="mb-3 flex-grow-1">
          
  <input type="checkbox" :checked="todo.checked"
  @change="toggleCheckbox" >

    <span class="ml-5" 
    :class="todo.checked ? 'text-muted' :''"
    :style="todo.checked ? 'text-decoration : line-through':''"
    >{{ todo.text }}</span>
        <v-btn outlined small icon class="btn-default" @click="deleteItem">X</v-btn>
      </div>
  
  </div>



</template>

<script>
export default {
    props:{
        todo : {
            type : Object,
            required : true
        }
    },
    methods :{
        toggleCheckbox(e){
            this.$emit('toggle-Checkbox',{
                id : this.todo.id,
                checked : e.target.checked
            })
        },
        deleteItem(){
            this.$emit("delete-item", this.todo.id)
        }
      
    }
}
</script>

<style>

</style>