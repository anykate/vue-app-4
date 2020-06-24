<template>
  <div class="addtodo">
    <form @submit.prevent="$emit('addNewTodo', newTodoObj)">
      <input
        v-if="edit_todo.name"
        type="text"
        v-model="edit_todo.name"
        class="form-control w-75 mx-auto"
      />
      <input v-else type="text" v-model="newTodoObj.name" class="form-control w-75 mx-auto" />
      <input
        v-if="edit_todo.name"
        type="submit"
        class="m-4 btn btn-outline-secondary"
        :value="update"
        @click="$emit('editFormTodo', edit_todo)"
      />
      <input v-else type="submit" class="m-4 btn btn-outline-secondary" :value="add" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodoForm",
  props: ["edit_todo"],
  data() {
    return {
      newTodoObj: {
        name: "",
        completed: false
      },
      add: "Add Todo",
      update: "Update Todo"
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.addtodo {
  margin: 30px 0;
  text-align: center;
}
</style>
