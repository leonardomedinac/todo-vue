<template>
  <div class="ui basic content center aligned segment">
    <button class="ui basic button icon" v-on:click="openForm" v-show="!isCreating">
      <i class="plus icon"></i>
    </button>
    <div class="ui centered card" v-show="isCreating">
      <div class="content">
        <div class="ui form">
          <div class="field">
            <label>Título</label>
            <input type="text" v-model="titulo" ref="title" defaultValue />
          </div>
          <div class="field">
            <label>Descripcion</label>
            <input type="text" v-model="descripcion" defaultValue />
          </div>
          <div class="ui two button attached buttons">
            <button class="ui basic blue button" v-on:click="sendForm">Crear</button>
            <button class="ui basic red button" v-on:click="closeForm">Cancelar</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            titulo: '',
            descripcion: '',
            isCreating: false
        }
    },
    methods: {
        openForm() {
            this.isCreating = true
        },
        closeForm() {
            this.isCreating = false;
        },
        sendForm() {
            if (this.titulo.length > 0 && this.descripcion.length > 0) {
                const titulo = this.titulo
                const descripcion= this.descripcion
                console.log('Titulo',titulo)
                this.$emit('create-todo',{
                    titulo,
                    descripcion,
                    estado: false
                })
                this.titulo = ''
                this.descripcion = ''
                this.isCreating = false;
            }
            this.isCreating = false;
        }
    },
}
</script>