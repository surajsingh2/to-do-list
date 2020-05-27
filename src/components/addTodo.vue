<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo.." autocomplete="off">
            <input type="submit" value="submit" class="btn">
        </form>
    </div>
</template>

<script>

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                title: this.title,
                completed: false
            }
            //Send up to Parent
            this.$emit('add-todo',newTodo);

            this.title = '';
        }
    }
}
</script>

<style  scoped>
   form {
       display: flex;
   }

   input[type="text"] {
       flex: 9;
       padding: 5px;
   }

   input[type="submit"] {
       flex:3;
   }
</style>