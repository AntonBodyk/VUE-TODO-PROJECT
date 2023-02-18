<template>
    <div class="app">
        <todo-header @create="addTask"/>
        <new-task :newtasks="newtasks"/>
        <completed-task/>
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
        addTask(task) {
              this.newtasks.push(task);
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
