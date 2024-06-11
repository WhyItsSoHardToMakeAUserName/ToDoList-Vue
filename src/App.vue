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
</style>