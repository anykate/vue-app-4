<template>
  <div class="container">
    <div class="row justify-content-between">
      <div
        class="col-md-6"
        @dblclick="$emit('editTodo', todo)"
        :class="{'is-completed':todo.completed}"
      >
        {{ todo.name }}
        <br />
        <br />
      </div>
      <div class="col-md-6">
        <div class="row">
          <div class="col-md-7">
            <button @click="$emit('toggleTodo', todo)" class="btn btn-outline-secondary">Toggle</button>
          </div>
          <div class="col-md-3">
            <button @click="$emit('deleteTodo', todo)" class="btn btn-outline-danger">Delete</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"]
};
</script>

<style>
.is-completed {
  text-decoration: line-through;
}
</style>