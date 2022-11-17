<template>
  <div>
      {{todo.checked}}
  <input type="checkbox" :checked="todo.checked"
  @change="toggleCheckbox" >
    <span class="mt-3">{{ todo.text }}</span>
  </div>
</template>

<script>
export default {
    props:{
        todo : {
            type : Object,
            reqires : true
        }
    },
    methods :{
        toggleCheckbox(e){
            this.$emit('toggle-Checkbox',{
                id : this.todo.id,
                checked : e.target.checked
            })
        }
    }
}
</script>

<style>

</style>