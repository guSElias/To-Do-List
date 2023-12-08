<template>
  <div>
    <p>Completed Tasks: {{ completedTasksCount }}</p>
    <p>Pending Tasks: {{ pendingTasksCount }}</p>
    <todo v-for="tarefa in tarefas" :key="tarefa.title" :tarefa="tarefa" 
      @complete-tarefa="completeTarefa"
      @delete-tarefa="deleteTarefa"/>
  </div>
</template>

<script >
import Todo from './Todo.vue';

export default {
  components: { Todo },
  props: ['tarefas'],
  computed: {
    completedTasksCount() {
      return this.tarefas.filter(tarefa => tarefa.done === true).length;
    },
    pendingTasksCount() {
      return this.tarefas.filter(tarefa => tarefa.done === false).length;
    },
  },
  methods: {
    completeTarefa(tarefa) {
      const tarefaIndex = this.tarefas.indexOf(tarefa)
      this.tarefas[tarefaIndex].done = true;
    },
    deleteTarefa(tarefa) {
  const tarefaIndex = this.tarefas.indexOf(tarefa);

  if (tarefaIndex !== -1) {
    this.tarefas.splice(tarefaIndex, 1);
  } else {
    console.warn('Tarefa não encontrada:', tarefa);
  }
}
  },
    
  }

</script>


<style>

</style>