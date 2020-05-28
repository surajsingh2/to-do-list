<template>
  <div class="todo-item p-3" v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input class="mr-4" type="checkbox" v-on:change="markComplete" />
      {{todo.title}}
      <button @click="$emit('del-todo',todo.id)" class="del">X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #343a40;
  color: #41b883f3;;
  text-align: left;
  border-bottom: 1px #ccc solid;
  font-size: 14px;
  letter-spacing: 2px;
  line-height: 1.6;
  font-weight: 100;
}

.is-complete {
  text-decoration: line-through;
}
input[type="checkbox"] {
  cursor: pointer;
}
.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>