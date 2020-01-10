<template>
    <div>
        <form @submit="addToDo">
            <input type="text" v-model="title" name="title" placeholder="Add to do ..." />
            <input type="submit" value="Submit" class="btn" />
        </form>
    </div> 
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

                this.$emit('add-todo', newTodo);
                this.title = "";
            }
        }
    }
</script>