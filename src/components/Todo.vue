<template>
  <div class='ui centered card'>
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ tarefa.title }}
      </div>
      <div class='meta'>
          {{ tarefa.project }}
          
      </div>
      <div class='extra content'>
          <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon'></i>
           </span>
           <span class='right floated trash icon' v-on:click="deleteTarefa(tarefa)">
            <i class='trash icon'></i>
          </span>
      </div>
    </div>
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="tarefa.title" />
        </div>
        <div class='field'>
          <label>Project</label>
          <input type='text' v-model="tarefa.project" />
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
    <div class='ui bottom attached green basic button' v-show="!isEditing && tarefa.done" >
        Completed
    </div>
    <div class='ui bottom attached red basic button' v-on:click="completeTarefa(tarefa)" v-show="!isEditing && !tarefa.done">
        Pending
    </div>
  </div>
</template>

<script>
export default {
  props: ['tarefa'],
  data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
  },
  hideForm(){ 
    this.isEditing = false;
    },
    deleteTarefa(tarefa){ 
      this.$emit('delete-tarefa', tarefa)
   },
   completeTarefa(tarefa) {
    this.$emit('complete-tarefa', tarefa);
   }
  }   
}
</script>

<style>

</style>