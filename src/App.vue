<template>
  <div id="app">  
    <Header/>
    <AddToDo v-on:add-todo="addToDo"/>
    <b-container fluid>
       <ToDoList v-bind:toDoList="toDoList" v-on:del-todo="deleteToDo"/>
    </b-container> 
  </div>
</template> 

<script> 
import Header from './components/layout/Header';
import ToDoList from './components/ToDoList';
import AddToDo from './components/AddToDo';
import axios from 'axios';
const url = "https://jsonplaceholder.typicode.com/todos";

export default { 
  name: 'app',
  components: { 
    Header,
    AddToDo,
    ToDoList
  },
  data() {
    return {
      toDoList: []
    }
  },
  methods: {
    deleteToDo(id) { 
      axios.delete(url+'/'+`${id}`)
        .then(res => res, this.toDoList = this.toDoList.filter(i => i.id !== id))
        .catch(err => alert('An error has occured in the delete request: '+ err.message)); 
    },
    addToDo(newItem) {
      const { title, completed } = newItem; 

      axios.post(url, { title, completed })
        .then(res => this.toDoList = [...this.toDoList, res.data])
        .catch(err => alert('An error has occured in the post request: '+ err.message));
    }
  },
  created() {
    axios.get(url+'?_limit=10')
      .then(res => this.toDoList = res.data)
      .catch(err => alert('An error has occured in the get request: '+ err.message));
  }
}
</script>

<style> 
</style>
