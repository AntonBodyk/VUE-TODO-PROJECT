<template>
    <div class="app">
        <todo-header @create="addTask"/>
        <new-task :newtasks="newtasks" :completedtasks="completedtasks" @remove="removeTask"/>
        <completed-task :completedtasks="completedtasks" :newtasks="newtasks" @remove="removeCompletedTask"/>
    </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import NewTask from './components/NewTask.vue';
import CompletedTask from './components/CompletedTask.vue';
    export default {
      components: {
        TodoHeader, NewTask, CompletedTask
      },
      data() {
        return {
          newtasks: [],
          completedtasks: []
        }
      },
      methods: {
        addTask(inputValue) {
              this.newtasks.push(inputValue);
          },
        removeTask(task) {
          this.newtasks = this.newtasks.filter(item => item.id !== task.id);
        },
        removeCompletedTask(task) {
          this.completedtasks = this.completedtasks.filter(item => item.id !== task.id)
        }
  }
}   
    
</script>

<style>
    body {
      font-family: 'Ubuntu', sans-serif;
      font-weight: 300;
    }
    .container {
      width: 800px;
      margin: 0 auto;
      padding: 0 15px;
    }
</style>
