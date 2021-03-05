<template>
    <ul>
        <li v-for="(titre, index) in tasks" :key="(titre, index)" class="list">
            <div>
                <p class="index">{{ index+1 }}. </p>
                <input type="checkbox" v-on:click="check(index)">
                <p v-bind:class="{'check': titre.checked}">{{titre.titre}}</p>
            </div>
            <button class="trash" v-on:click='remover(index)'>🚮</button>
        </li>
    </ul>
</template>

<script>
export default {
    name: 'todolist',
    props: ['tasks'],
    methods: {
        remover(index) {
            this.$emit('numberIndexRemove', index)
        },

        check(index) {
            this.$emit('checked', index)
        }
    }
}
</script>

<style>
    .list {
        display: flex;
        align-items: center;
        margin-left: 25px;
        justify-content: space-between;
        height: 40px;
    }

    .list div {
        display: flex;
        align-items: center;
    }

    .list input {
        margin-right: 25px;
    }

    .trash {
        margin-right: 25px;
    }

    .index {
        margin-right: 25px;
    }

    .check {
        text-decoration: line-through;
    }

    input:focus {
        outline: none;
    }
</style>