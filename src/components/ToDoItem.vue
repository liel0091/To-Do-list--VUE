<template>
    <b-list-group-item variant="secondary" class="mb-1 d-flex justify-content-between" href="#" v-bind:class="{'is-complete':item.completed}"> 
        <input class="mr-2" type="checkbox" v-on:change="markComplete"/> 
        <small>{{item.title}}</small> 
        <b-button pill variant="danger" @click="$emit('del-todo', item.id)">
            <b-icon icon="x"/>
        </b-button> 
    </b-list-group-item>
</template>

<script>
    export default {
        name: "ToDoItem",
        props: ["item"],
        methods: {
            markComplete() {
                this.item.completed = !this.item.completed;
            }
        }
    }
</script>

<style scoped> 
    .is-complete{
        text-decoration: line-through;
    } 
</style>