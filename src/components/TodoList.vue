// Html
<template>
  <div>
    <p class="tareas">Tareas completadas: {{todos.filter(todo => todo.estado === true).length}}</p>
    <p class="tareas">Tareas pendientes: {{todos.filter(todo => todo.estado === false).length}}</p>
    <div class="list-todo">
      <ToDo
        v-on:complete-todo="completeTodo"
        v-on:delete-todo="deleteTodo"
        v-for="todo in todos"
        v-bind:todo="todo"
        :key="todo.id">
      </ToDo>
    </div>
  </div>
</template>

// JS
<script>
import ToDo from "./ToDo";
import sweetalert from "sweetalert";

export default {
  props: ["todos"],
  components: {
    ToDo
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
      sweetalert("Borrado", "To-Do eliminado.", "success");
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].estado = true;
      sweetalert("Bien", "¡To-Do completado!", "success");
    }
  }
};
</script>

// Estilos
<style>
.tareas {
  text-align: center;
}
.list-todo {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
</style>