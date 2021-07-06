<template>
<div class="container">
  <Header v-on:toggle-add-task="toggleAddTask" title="Task Tracker" v-bind:showAddTask="showAddTask"/>
  <div v-show="showAddTask">
    <AddTask v-on:add-task="addTask"/>
  </div>
  <Tasks v-on:toggle-reminder="toggleReminder" v-on:delete-task="deleteTask" v-bind:tasks="tasks"/>
</div>
</template>

<script>
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data(){
    return{
      tasks:[],
      showAddTask: false,
    }
  },
  methods:{
    toggleAddTask(){
      this.showAddTask = !this.showAddTask;
    },
    addTask(task){
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id){
      if(confirm('Are you sure?')){
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task);
    }
  },
  created(){
    this.tasks = [
    ]
  }
}
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
</style>
