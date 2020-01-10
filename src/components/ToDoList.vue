<template>
    <div class="mt-5"> 
        <b-list-group v-bind:key="item.id" v-for="item in toDoList"> 
            <ToDoItem v-bind:item="item" v-on:del-todo="$emit('del-todo', item.id)"/>
        </b-list-group>
    </div>  
</template>

<script>
    import ToDoItem from './ToDoItem';
    
    export default {
        name: "ToDoList",
        components: {
            ToDoItem
        },
        props:["toDoList"] 
    }
</script>

<style scoped>

</style>