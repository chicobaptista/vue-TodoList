<template>
  <div class="row">
    <div class="columns">
      <div class="column">
        <div 
          v-for="(tarefa, index) in tarefas" 
          class="field is-grouped">
          <p class="control">
            <a 
              class="button is-rounded is-small check-button"
              @click="check(index)">
              <span class="icon is-small"/>
            </a>
          </p>
          <p 
            :class="{'checked': tarefa.checked}"
            class="control is-expanded">{{ tarefa.description }}</p>
          <p class="control">
            <a 
              class="button is-danger is-small"
              @click="remover(index)">
              <span class="icon is-small">
                <i class="fa fa-trash"/>
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
  name: 'TodoList',
  props: {
      tarefas: {
          default: function () { return [] },
          type: Array,
          }
  },
  data () {
    return {
    }
  },
  methods: {
      check(index) {
          this.$emit('check', index)
      },
      remover(index) {
          this.$emit('remover', index)
      }
  }
}
</script>

<style scoped>
.button {
  border-radius: 50%;
}
.checked {
  text-decoration: line-through;
}
</style>