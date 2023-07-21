<template>
      <div class="row justify-content-center">
      <div class="col-11">
        <img src="./../assets/logo.png" alt="Vue-Logo" class="d-block mx-auto">
        <form @submit.prevent="addItems">
          <label>New Task</label>
          <input type="text" class="form-control mt-1" v-model="task">
          <button class="btn btn-dark mt-3" type="submit">Add New Task</button>
        </form>
      </div>
    </div>
</template>

<script>
export default {
  name : "AddTask",
  data: ()=>({
    task : "",
  }),
  methods :{
    addItems(){
      if(this.task.length === 0){
        return alert("You Need To Fill the Task!")
      }
      const taskItems = {
        task : this.task,
        completed : false,
      };
      this.$emit("addTask",taskItems);
      this.task = "";
       this.$notify({
        group: 'foo',
        title: 'Make A Task',
        text: 'Hello user! You just make a task 😎',
        type: 'info',
      });
    },
  }
}
</script>

<style>

</style>