<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>{{showCompletion}}</h1>
    <ToDo :todos="todos" @compChange="toDoStatus" @delEntry="deleteEntry"/>
    <TaskForm :todos="todos" />
  </div>
</template>

<script>
import ToDo from './components/ToDo.vue'
import TaskForm from './components/TaskForm.vue'

export default {
  name: 'app',
  components: {
    ToDo,
    TaskForm
  },
  data() {
    return {
      showCompletion: "",
      todos:[
        {title:"things", desc:"do things", status:false},
        {title:"stuff", desc:"do stuff", status:false},
        {title:"other things", desc:"do other things", status:false}
      ]
    }
  },
  watch: {
    todos() {
      this.toDoStatus();
    },
  },
  methods: {
    toDoStatus() {
      let tasksDone = this.todos.every(val => val.status==true);
      if(tasksDone==true){
        this.showCompletion = "All Done";
      }else{
        this.showCompletion = "More stuff to do!";
      }
    },
    deleteEntry(key){
      this.todos.splice(key,1);
    }
  },
  mounted(){
    this.toDoStatus();
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
