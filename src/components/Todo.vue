<template>
  <div class="ui card todo">
    <div class="content" v-show="!isEditing">
      <div class="header">{{ todo.titulo }}</div>
      <div class="meta">{{ todo.descripcion }}</div>
      <div class="extra content">
        <button class="ui right floated edit icon button" v-on:click="showForm">
          <i class="edit icon"></i>
        </button>
        <button class="ui right floated edit icon button" v-on:click="deleteTodo(todo)">
          <i class="trash icon"></i>
        </button>
      </div>
    </div>
    <div class="content" v-show="isEditing">
      <div class="ui form">
        <div class="field">
          <label>Título</label>
          <input type="text" v-model="todo.titulo" />
        </div>
        <div class="field">
          <label>Descripcion</label>
          <input type="text" v-model="todo.descripcion" />
        </div>
        <div class="ui two button attached buttons">
          <button class="ui basic blue button" 
                  v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
    <div class="ui bottom attached green button"
        v-show="!isEditing && todo.estado"
        disabled>
          Finalizado
    </div>
    <div class="ui bottom attached red button"
          v-on:click="completeTodo(todo)"
          v-show="!isEditing && !todo.estado">
          Pendiente
    </div>
  </div>
</template>

<script>
export default {
  props: ["todo"],
  data() {
    return {
      isEditing: false
    };
  },
  methods: {
    showForm() {
      this.isEditing = true
    },
    hideForm() {
      this.isEditing = false
    },
    deleteTodo(todo){
      this.$emit('delete-todo', todo)
    },
    completeTodo(todo) {
      this.$emit('complete-todo', todo)
    }
  }
};
</script>
<style>
.todo {
  margin: 10px 20px !important;
}
</style>