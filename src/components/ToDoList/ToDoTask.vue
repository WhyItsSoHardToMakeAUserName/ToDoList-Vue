<template>
    <div style="display: flex;align-items: center; gap: 10px;padding: 5px 0;">
        <input type="checkbox"  @click="toggleTagOnCheckbox">

        <component :is="CurrentTag" ref="text"id="text" @click="setEditingState" @focusout="removeEditingState"><slot></slot></component>
        
        <VButton @click="$emit('deleteTask')">delete</VButton>
    </div>
</template>
<script>
export default {
    emits:['deleteTask'],
    data(){
        return{
            CurrentTag:'p',
            PreviousTag:'',
        }
    },
    methods:{
        test(){
            console.log("helo")
        },
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
</style>