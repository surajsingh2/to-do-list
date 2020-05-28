<template>
  <div>
    <form @submit="addTodo" class="mx-3">
      <input type="text" v-model="title" name="title" placeholder="Add Todo.." autocomplete="off" />
      <input type="submit" value="Add" class="btn btn-primary" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        title: this.title,
        completed: false
      };
      //Send up to Parent
      this.$emit("add-todo", newTodo);

      this.title = "";
    }
  }
};
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
  flex: 2;
}
.btn-primary {
  color: #fff;
  background-color: #41b882;
  border-color: #41b882;
}
.btn-primary:hover {
  color: #fff;
  background-color: #35495e;
  border-color: #35495e;
}


</style>