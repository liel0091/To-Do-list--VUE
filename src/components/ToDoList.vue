<template>
<div>
    <h1>To Do List</h1>
    <ul v-bind:key="item.id" v-for="item in toDoList"> 
       <ToDoItem v-bind:item="item" v-on:del-todo="$emit('del-todo', item.id)"/>
    </ul>
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