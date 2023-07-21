<template>
  <div class="container">
    <notifications group="foo" class="mt-2"/>
    <AddTaskVue @addTask="addTask"/>
    <transition-group class="row justify-content-center mt-3"
    enter-active-class="animate__animated animate__backInLeft"
    leave-active-class="animate__animated animate__backOutRight">  
     <TodoItemsVue v-for="(todo,index) in todos" :key="index" :todo="todo" :index="index" @completeTask="completeTask" @removeTask = "removeTask" />
    </transition-group>
  </div>
</template>

<script>
import AddTaskVue from './components/AddTask.vue';
import TodoItemsVue from './components/TodoItems.vue';

export default {
  name: 'App',
  components :{
    AddTaskVue,TodoItemsVue
  },
  data : ()=>({
    todos : [],
  }),
  methods :{
    addTask(taskItems){
      this.todos.push(taskItems);
    },
    removeTask(index){
      if(confirm("Are You Sure To Delete This Task? ")){
        this.todos.splice(index,1)
         this.$notify({
        group: 'foo',
        title: 'Deleted!',
        text: 'Hello user! Your Task has been removed 👌',
        type: 'error',
      });
      }
    },
    completeTask(index){
      this.todos[index].completed = true;
      this.$notify({
        group: 'foo',
        title: 'Completed!',
        text: 'Hello user! Your Task is completed 😉',
        type: 'success',
      });
    },
  }
}
</script>

<style>
img{
  width: 130px;
  margin-top: 10%;
  margin-bottom: 30px;
}
label{
  color: #fff;
}
.btn-c{
  margin-right: 10px;
  display: inline-block;
}
.card{
  border-radius: 1rem !important;
}
.done{
  text-decoration: line-through;
  text-decoration-thickness: 2px;
}
span{
  font-size: 20px;
}
</style>
