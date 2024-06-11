<template>
    <div class="container">

        <h1>To do list</h1>

        <div class="NewTaskDiv">
            <input style="width: 70%;" v-model="NewTask" @keydown.enter="addNewTask" type="text">
            <VButton @click="addNewTask">Add</VButton>
        </div>

        <div v-for="Task in Tasks" :key=Task.id>
            <ToDoTask @deleteTask="deleteTask(Task.id)" :task="Task"></ToDoTask>
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
                    text:'Breathe air',
                    done:true
                },
                {
                    id:2,
                    text:'Write todays tasks',
                    done:false
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
                    text:this.NewTask,
                    done:false
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
<style>
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
        border-radius: 20px;
        border:  2px solid rgb(153, 153, 153);
        padding-left: 10px;
    }
    .NewTaskDiv{
        display: flex;
        justify-content: space-between;
    }
</style>