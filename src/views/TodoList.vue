<template>
  <div>
    <h1>Todo List</h1>
    <TodoForm @submit.prevent="addTodo">
      <h2 slot="title">Add a Todo</h2>
      <p slot="desc">Your Todo will be saved</p>
    </TodoForm>
    <Todo :todos="todoList" @removeTodo="appDeleteTodo" />
  </div>
</template>
<script>
import Todo from "@/components/Todo.vue";
import TodoForm from "@/components/TodoForm.vue";

export default {
  data() {
    return {
      todoList: ["Walk the dogs", "Go for a ride"]
    };
  },
  components: {
    Todo,
    TodoForm
  },
  methods: {
    appDeleteTodo(index) {
      this.todoList.splice(index, 1);
    },
    addTodo(todo) {
      this.todoList.push(todo);
    }
  }
};
</script>

<style>
ul {
  list-style: none;
  width: 50%;
  margin: 0 auto;
}
ul li {
  border-bottom: 1px solid #acacac;
  padding: 10px 0;
  margin-bottom: 10px;
}
</style>
