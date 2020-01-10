<template>
    <span v-bind:class="{'is-complete':item.completed}"> 
        <p>
            <input type="checkbox" v-on:change="markComplete"/>
            {{item.title}} 
            <button @click="$emit('del-todo', item.id)">x</button>
        </p>
    </span>
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