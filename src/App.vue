<template>
  <div class="container">
    <notifications group="foo" />
    <div class="row justify-content-center">
      <div class="col-11">
        <img src="./assets/logo.png" alt="Vue-Logo" class="d-block mx-auto">
        <form @submit.prevent="addItems">
          <label>New Task</label>
          <input type="text" class="form-control mt-1" v-model="task">
          <button class="btn btn-dark mt-3" type="submit">Add New Task</button>
        </form>
      </div>
    </div>
    <div class="row justify-content-center mt-3">
      <div class="col-11 mt-3" v-for="(todo,index) in todos" :key="index" >
        <div class="card">
          <div class="row p-3 align-items-center">
            <div class="col-7">
            <span :class="{done : todo.completed}">{{todo.task}}</span> 
            </div>
            <div class="col text-end">
              <button class="btn btn-success mr-3 btn-c" @click="completeTask(index)"><i class="material-icons mt-1">check</i></button>
              <button class="btn btn-danger" @click="removeTask(index)"><i class="material-icons mt-1">delete</i></button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data : ()=>({
    task : "",
    todos : [],
  }),
  methods :{
    addItems(){
      this.todos.push({task:this.task,completed:false});
      this.task = "";
    },
    removeTask(index){
      this.todos.splice(index,1)
      this.$notify({
        group: 'foo',
        title: 'Deleted!',
        text: 'Hello user! Your Task has been removed!',
        type: 'warn',
      });
    },
    completeTask(index){
      this.todos[index].completed = true;
      this.$notify({
        group: 'foo',
        title: 'Completed!',
        text: 'Hello user! Your Task is completed!',
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
}
span{
  font-size: 20px;
}
</style>
