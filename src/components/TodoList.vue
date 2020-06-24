<template>
  <div class="container">
    <add-todo-form
      :edit_todo="edit_todo"
      @addNewTodo="addNewToDo"
      @editFormTodo="updateButtonClicked"
    ></add-todo-form>
    <div class="row justify-content-center mb-5">
      <div class="col-md-8 d-flex justify-content-center">
        <ul class="list-group">
          <li class="list-group-item" v-for="(todo, index) in todos" :key="index">
            <todo-item
              :todo="todo"
              @deleteTodo="deleteToDo(todo)"
              @editTodo="editToDo(todo)"
              @toggleTodo="toggleToDo(todo)"
            ></todo-item>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import TodoItem from "@/components/TodoItem.vue";
import AddTodoForm from "@/components/AddTodoForm.vue";

export default {
  name: "TodoList",
  components: {
    "todo-item": TodoItem,
    "add-todo-form": AddTodoForm
  },
  data() {
    return {
      todos: [
        { name: "Bring Milk", completed: false },
        { name: "Bring Sugar", completed: false },
        { name: "Bring Tea", completed: true },
        { name: "Have Dinner", completed: false },
        { name: "Sleep", completed: true }
      ],
      edit_todo: ""
    };
  },
  methods: {
    deleteToDo(this_todo) {
      console.log("delete clicked - " + this_todo.name);
      this.todos = this.todos.filter(todo => todo.name !== this_todo.name);
    },
    toggleToDo(this_todo) {
      //   if (!this_todo.completed) {
      //     console.log("marked completed - " + this_todo.name);
      //     this_todo.completed = !this_todo.completed;
      //   }
      console.log("toggle completed - " + this_todo.name);
      this_todo.completed = !this_todo.completed;
    },
    editToDo(this_todo) {
      this.edit_todo = this_todo;
      console.log("double clicked - " + this_todo.name);
    },
    updateButtonClicked(this_todo) {
      console.log("update button clicked - " + this_todo.name);
      this.edit_todo = "";
    },
    addNewToDo(todo) {
      if (todo.name) {
        this.todos.unshift({
          name: todo.name,
          completed: todo.completed
        });
        todo.name = "";
      }
    }
  }
};
</script>

<style>
ul {
  list-style-type: none;
  width: 100%;
}
</style>