<template>
    <div id="card">
        <div id="haut">
            <div id="date">{{ date }}</div>
            <div id="msg"><h2>{{ msg }}</h2></div>
            <div id="numberTask">{{ numberTask }} tâches</div>
        </div>
        <new-todo @custom-event-name='setMessage'></new-todo>
        <todo-list :tasks="tasks" @numberIndexRemove='removeTask' @checked='check'></todo-list>
    </div>
</template>

<script>
import newTodo from './new-todo.vue'
import TodoList from './todo-list.vue'
export default {
  components: { newTodo, TodoList },
    name: "card",
    data() {
        return {
            msg: "VueJs Tutorial ToDo List",
            numberTask: 0,
            tasks: [],
        }
    },
    methods: {
        setMessage(payload) {
            this.tasks.push({titre: payload, checked:false})
            this.numberTask++
        },

        removeTask(payload) {
            this.tasks.splice(payload, 1)
            this.numberTask--
        },

        check(index) {
            if(this.tasks[index].checked === false) {
                this.tasks[index].checked = true;
            } else {
                this.tasks[index].checked = false;
            }
            
        }
    },
    computed: {
        date: function() {
        let current = new Date();
        let day = current.toLocaleString('default', { weekday: 'long' })
        let month = current.toLocaleString('default', { month: 'long' })
        let date = current.getDate();
        let dateTime = day +' '+ date + ' ' + month ;

      return dateTime;
        },
    }
}
</script>

<style>
    #card {
        background-color: whitesmoke;
        width: 800px;
        min-height: 400px;
        margin: auto;
        border-radius: 10px;
    }

    #haut {
        display: flex;
        align-items: center;
        justify-content: space-around;
        box-shadow: grey 0px 2px 6px;
        height: 50px;
        font-weight: bold;
    }

    #msg h2 {
        color: teal;
        font-weight: bold;
    }

    input:focus {
        outline: none;
    }
</style>