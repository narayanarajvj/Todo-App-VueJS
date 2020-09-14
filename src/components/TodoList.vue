<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <p class="display-4">My TODO List</p>
      </div>
    </div>
    <div class="row">
      <div class="col-12 col-lg-6 mb-2">
        <NewTodo @on-addtodo="addTodo($event)" />
      </div>
    </div>
    <div class="row">
      <div class="col-12 col-lg-6">
        <ul class="list-group">
          <Todo
            v-for="(todo, index) in todos"
            :key="index"
            :todoString="todo.todoString"
            :completed="todo.completed"
            @on-delete="deleteTodo(todo)"
            @on-toggle="toggleTodo(todo)"
            @on-edit="editTodo(todo, $event)"
          />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./Todo";
import NewTodo from "./NewTodo";
export default {
  components: {
    Todo,
    NewTodo
  },
  data() {
    return {
      todos: [
        { todoString: "MERN", completed: false },
        { todoString: "Python", completed: true },
        { todoString: "Graph Database", completed: true },
        { todoString: "Adv. JavaScript", completed: false }
      ]
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({
        todoString: newTodo,
        completed: false
      });
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
    },
    editTodo(todo, newTodoString) {
      todo.todoString = newTodoString;
    },
    deleteTodo(deleteTodo) {
      this.todos = this.todos.filter(todo => todo !== deleteTodo);
    }
  }
};
</script>


<style >
</style>