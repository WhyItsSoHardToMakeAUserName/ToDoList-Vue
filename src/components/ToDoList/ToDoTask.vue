<template>
    <div>
        <input type="checkbox" v-model="task.done"  @click="toggleTagOnCheckbox">

        <component :is="CurrentTag" ref="text"id="text" :value="task.text" @input="task.text = $event.target.value" @click="setEditingState" @keydown.enter="removeEditingState" @focusout="removeEditingState">{{ task.text }}</component>
        
        <VButton @click="$emit('deleteTask')">delete</VButton>
    </div>
</template>
<script>
export default {
    emits:['deleteTask'],
    props:{
        task:Object
    },
    data(){
        return{
            CurrentTag:this.task.done === false? 'p' :'del',
            PreviousTag:'',
        }
    },
    methods:{
        toggleTagOnCheckbox(){
            this.CurrentTag = this.CurrentTag === 'p' ? 'del' : 'p'
        },
        setEditingState(){
            if(this.CurrentTag != 'input'){
                this.PreviousTag = this.CurrentTag
            }
            this.CurrentTag = 'input'
            this.$nextTick(() => {
                    this.$refs.text.focus();
                });
        },
        removeEditingState(){
            this.CurrentTag = this.PreviousTag
        }
    }
}
</script>
<style scoped>
    p{
        margin: 0;
    }
    div{
        display: flex;
        align-items: center; 
        gap: 10px;
        padding: 5px 0;
    }
</style>