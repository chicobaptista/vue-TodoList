<template>
  <div class="row">
    <div class="collumns">
      <div class="collumn is-half is-offset-one-quarter">
        <div class="field is-grouped">
          <p class="control is-expanded">
            <input 
              v-model="tarefa" 
              class="input is-primary has-text-centered" 
              type="text" 
              placeholder="Nova Tarefa">
          </p>
          <p class="control">
            <a class="button is-success add-button" @click="enviarTarefa">
              <span class="icon is-small">
                <i class="fa fa-plus"/>
              </span>
            </a>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NovoTodo",
  data() {
    return {
      tarefa: ""
    };
  },
  methods: {
      enviarTarefa() {
          // emita evento contendo a string de nova tarefa
          if (this.tarefa != '') {
              this.$emit('novaTarefa', this.tarefa)
          }
          // limpa campo de tarefa
          this.tarefa = '';
      }
  }
};
</script>

<style scoped>
.input {
  border-left: 0;
  border-right: 0;
  border-top: 0;
  border-radius: 0;
  outline: none;
  border-bottom-width: 2px;
  box-shadow: none;
}

.input.is-primary:focus {
  box-shadow: none;
}
.add-button {
  border-radius: 50%;
}
</style>

