<template>
  <div>
    <h1 class="ui dividing centered header">Lista de ToDo's</h1>
    <CreateToDo v-on:create-todo="addTodo"></CreateToDo>
    <ToDoList v-bind:todos="todos"></ToDoList>
  </div>
</template>

<script>
import ToDoList from "./components/ToDoList";
import CreateToDo from "./components/CreateToDo";
import sweetalert from "sweetalert";

export default {
  name: "App",
  components: {
    ToDoList,
    CreateToDo
  },
  data() {
    return {
      todos: [
        {
          titulo: "Poner alarma",
          descripcion: "Configurar hora adecuada",
          estado: false
        },
        {
          titulo: "Desayunar",
          descripcion: "Preparar dieta adecuada",
          estado: true
        },
        {
          titulo: "Tomar el bus",
          descripcion: "Verificar pasaje",
          estado: true
        }
      ]
    };
  },
  methods: {
    addTodo(todo) {
      sweetalert("Creado!", "To-Do creado correctamente", "success");
      this.todos.push(todo);
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  margin-top: 10px !important;
}
</style>
