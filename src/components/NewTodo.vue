<template>
    <input v-model="task" id="input" class="input" type="text" placeholder="Add task">
    <span v-on:click="addTask" class="icon has-text-success">
        <i class="fas fa-check-square fas fa-2x"></i>
        </span>
</template>

<style scoped>
    input{
        width: 30%;
        margin: 2%;
    }
    span{
        margin-top: 2.5%;
    }
</style>

<script>
export default {
    name: 'newtodo',

    data(){
      return {
          task: " "
          }
    },
    methods: {
        addTask(){
           this.$emit('newTask', this.task)
           document.getElementById("input").value = "";
        }
    }
}
    
</script>