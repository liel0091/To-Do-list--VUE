<template>   
    <b-card bg-variant="light"> 

        <label for="input-large">Add task:</label> 
        <b-form @submit="addToDo" class="d-flex justify-content-between"> 
            <b-form-input id="input-large" size="lg" type="text" v-model="title" name="title" placeholder="Add to do ..." />
            <b-button variant="warning" class="ml-2" type="submit">Submit</b-button>
        </b-form>   
    </b-card>  
</template>

<script> 
    export default {
        name: "AddToDo",
        data() {
            return {
                title:''
            }
        },
        methods: {
            addToDo(e) {
                e.preventDefault();  

                const newTodo = { 
                    title: this.title,
                    completed: false
                } 

                if(newTodo.title){
                    this.$emit('add-todo', newTodo);
                    this.title = "";
                }else {
                    alert('Please describe your task')
                } 
            }
        }
    }
</script>