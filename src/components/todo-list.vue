<template>
    <button v-on:click='deleteAll()'>Tout supprimer</button>
    <button v-on:click='deleteSelect()'>Supprimer tâches séléctionés</button>
    <ul>
        <li v-for="(titre, index) in tasks" :key="(titre, index)" class="list">
            <div>
                <p class="index">{{ index+1 }}. </p>
                <input type="checkbox" v-on:click="check(index)" v-if="titre.checked === true" checked>
                <input type="checkbox" v-on:click="check(index)" v-if="titre.checked === false">
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
        },

        deleteAll() {
            this.$emit('deleteAll')
        },
        
        deleteSelect() {
            this.$emit('deleteSelect')
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