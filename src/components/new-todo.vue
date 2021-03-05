<template>
    <div id="addTodoDiv">
        <input v-model="message" type="text" id="addTodo" placeholder="Nouvelle tâche">
        <button id="addTodoButton" v-on:click='newtask()'>+</button>
    </div>
</template>

<script>
    export default {
        name: "todo",
        data() {
            return {
                message: '',
            }
        },
        methods: {
            newtask() {
                this.$emit('custom-event-name', this.message)
                document.getElementById('addTodo').value = ''
            },
        }
    }
</script>

<style>

    #addTodoDiv {
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 25px 0;
    }

    #addTodo {
        height: 29px;
        border: none;
        background-color: whitesmoke;
        border-bottom: turquoise solid 2px;
        text-align: center;
        margin: 0 20px;
    }

    #addTodoButton {
        background-color: green;
        width: 40px;
        height: 40px;
        border-radius: 50%;
        font-size: 24px;
        border: none;
        display: flex;
        justify-content: center;
        color: white;
    }

    input:focus, button:focus {
        outline: none;
    }
</style>