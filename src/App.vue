<template>
  <div id="app">  
    <Header/>
    <AddToDo v-on:add-todo="addToDo"/>
    <ToDoList v-bind:toDoList="toDoList" v-on:del-todo="deleteToDo"/>
  </div>
</template> 

<script> 
import Header from './components/layout/Header';
import ToDoList from './components/ToDoList';
import AddToDo from './components/AddToDo';
import axios from 'axios';

export default {
  name: 'app',
  components: { 
    Header,
    AddToDo,
    ToDoList
  },
  data() {
    return {
      toDoList: [
        {
          id: 1, 
          title: "First",
          completed: false
        },
         {
          id: 2, 
          title: "Second",
          completed: true
        },
         {
          id: 3, 
          title: "Third",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteToDo(id) { 
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => res, this.toDoList = this.toDoList.filter(i => i.id !== id))
        .catch(err => alert('An error has occured in the delete request: '+ err.message)); 
    },
    addToDo(newItem) {
      const { title, completed } = newItem; 

      axios.post('https://jsonplaceholder.typicode.com/todos', { title, completed })
        .then(res => this.toDoList = [...this.toDoList, res.data])
        .catch(err => alert('An error has occured in the post request: '+ err.message));
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => this.toDoList = res.data)
      .catch(err => alert('An error has occured in the get request: '+ err.message));
  }
}
</script>

<style> 
</style>
