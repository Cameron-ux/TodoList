<template>
    <ul>
        <li class="list" v-bind:class="{'taskDone':task.checked}" v-for="(task, index) in tasks" :key="(task, index)">
        <input v-on:click="trait(index)" type="checkbox"/>
        {{task.description}}
        <button v-on:click="deleteTask(index)" class="delete is-medium"></button>
        </li>
    </ul>
</template>
<style scoped>
    .list{
        display: flex;
        justify-content: space-around;
        margin-bottom: 1%;
    }

    .taskDone{
        text-decoration: line-through;
    }
</style>

<script>
export default {
    name: 'todolist',
    props: ['tasks'],

    methods: {
        deleteTask(index){
           this.$emit('deleteTask', index)
        },
        trait(index){
           this.$emit('trait', index)
        }
}
}
</script>