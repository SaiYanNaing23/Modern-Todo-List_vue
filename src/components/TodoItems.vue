<template>
   <div class="col-11 mt-3" >
        <div class="card">
          <div class="row p-3 align-items-center">
            <div class="col-7"
            :class="{done : todo.completed}" >
            <input type="text" class="form-control">
            {{todo.task}}
            </div>
            <div class="col text-end">
              <button class="btn btn-success mr-3 btn-c" @click="completeTask(index)"><i class="material-icons mt-1">check</i></button>
              <button class="btn btn-danger" @click="removeTask(index)"><i class="material-icons mt-1">delete</i></button>
            </div>
          </div>
        </div>
    </div>
</template>

<script>
export default {
    name : "TodoItems",
    props : ["todo","index"],
    methods : {
        completeTask(index){
            this.$emit("completeTask",index)
        },
        removeTask(index){
            this.$emit( "removeTask",index)
        }
    }
}
</script>

<style>

</style>