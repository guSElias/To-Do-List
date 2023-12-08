<template>
  <todo-list v-bind:tarefas="tarefas"/>
  <create-todo v-on:create-tarefa="createTarefa"/>
</template>

<script>
import CreateTodo from './components/CreateTodo.vue'
import TodoList from './components/TodoList.vue'

export default {

  components: { 
     TodoList,
     CreateTodo },

  name: 'App',
    data() {
    return {
      tarefas: [{
        title: 'Tarefa A',
        project: 'Projeto A',
        done: false,
      }, {
        title: 'Tarefa B',
        project: 'Projeto B',
        done: true,
      }, {
        title: 'Tarefa C',
        project: 'Projeto C',
        done: false,
      }]
    }
  },
  methods: {
    createTarefa(title, project) {
      debugger
      this.tarefas.push({
        title,
        project,
        done: false
      })
    }
  }
}
</script>

<style>

</style>