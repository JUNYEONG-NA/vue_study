<template>
  <div>
      <div>
      {{todo.checked}}
  <input type="checkbox" :checked="todo.checked"
  @change="toggleCheckbox" >
    <span class="mt-3">{{ todo.text }}</span>
      </div>
    <div> 
        <button @click="setStatus"> {{name}}는{{status}}</button>
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
    data(){
        return{
            name : "지우",
            status : "귀여움"
        }
    },
    methods :{
        toggleCheckbox(e){
            console.log(e.target.checked)
            console.log(this.todo.id)
            
            this.$emit('toggle-Checkbox',{
                id : this.todo.id,
                checked : e.target.checked
            })
        },
        setStatus(){
            this.status = "바보"
        }
    }
}
</script>

<style>

</style>