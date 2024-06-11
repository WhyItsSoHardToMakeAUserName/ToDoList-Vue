<template lang="">
  <div class="BASE">
    <ToDoList></ToDoList>
  </div>
</template>
<script>
import ToDoList from './components/ToDoList/ToDoList.vue';
export default {
  components:{
    ToDoList
  }
}
</script>
<style>
  .BASE{
    display: flex;
    justify-content: center;
    align-items: center;
    padding-top: 5%;
  }
  input{
        border-radius: 20px;
        border:  2px solid rgb(153, 153, 153);
        padding-left: 10px;
    }
</style>