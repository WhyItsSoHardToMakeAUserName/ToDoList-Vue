<template>
    <div>
        <div v-for="Task in Tasks" :key=Task.id>
            <ToDoTask>{{ Task.text }}</ToDoTask>
        </div>
    </div>
</template>
<script>
import ToDoTask from './ToDoTask.vue';
export default {
    components:{
        ToDoTask
    },  
    data(){
        return{
            Tasks:[
                {
                    id:1,
                    text:'hello'
                },
                {
                    id:2,
                    text:'hello'
                }
            ]
        }
    }
}
</script>
<style scoped>
    
</style>