<template>
    <section class="todo">
        <nav>
            <h1>{{ date }}</h1>
            <h1 class="tuto">VueJS Tuto TodoList</h1>
            <h1>{{tasks.length}} Tâche(s)</h1>
        </nav>
        <new-todo @newTask="showTask"></new-todo>
        <todo-list @deleteTask="noTask" @trait="taskDone" :tasks="tasks"></todo-list>
    </section>
</template>

<style scoped>
    nav {
        display: flex;
        justify-content: space-around;
        box-shadow: 0px 2px 6px grey;
    }

    .todo {
        background-color: white;
        border-radius: 5px;
        box-shadow: 5px 5px 20px grey;
    }

    h1 {
        font-size: 1.5em;
    }

    .tuto {
        color: #05D3B5;
    }
</style>

<script>
    import NewTodo from './NewTodo.vue';
    import TodoList from './TodoList.vue';

    export default {
        name: 'todocard',
        components: {
            NewTodo,
            TodoList
        },
        data() {
            return {
                tasks: []
            }
        },
        computed: {
            date: function () {
                let current = new Date();
                let day = current.toLocaleString('default', {
                    weekday: 'long'
                })
                let month = current.toLocaleString('default', {
                    month: 'long'
                })
                let date = current.getDate();
                let dateTime = day + ' ' + date + ' ' + month;

                return dateTime;
            },
        },
        methods: {
            showTask(task) {
                this.tasks.push({
                    description: task,
                    checked: false
                })
            },
            noTask(no) {
                this.tasks.splice(no, 1)
            },
            taskDone(done) {
                if (this.tasks[done].checked === false) {
                    this.tasks[done].checked = true
                } else {
                    this.tasks[done].checked = false
                }
            }
        }

    }
</script>