<template>
    <div class="container">
        <h1>To do list</h1>
        <div style="display: flex; justify-content: space-between">
            <input v-model="NewTask" type="text">
            <VButton @click="addNewTask">Add</VButton>

        </div>
        <div v-for="Task in Tasks" :key=Task.id>
            <ToDoTask @deleteTask="deleteTask(Task.id)" :task="Task">{{ Task.text }}</ToDoTask>
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
            ],
            NewTask:''
        }
    },
    methods:{
        addNewTask(){
            if(this.NewTask!=''){
                this.Tasks.push({
                    id:Date.now(),
                    text:this.NewTask
                })
                this.NewTask = ''
            }
        },
        deleteTask(id){
            this.Tasks = this.Tasks.filter(task => task.id !== id)
        }
    }
} 
</script>
<style scoped>
    h1{
        font-family: Arial, Helvetica, sans-serif;
        color: rgb(39, 39, 39)
    }
    .container{
        display: flex;
        max-width: 400px;
        min-width: 400px;
        flex-direction: column;
        
    }
    input{
        width: 70%;
    }
</style>