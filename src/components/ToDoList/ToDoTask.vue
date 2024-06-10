<template>
    <div style="display: flex;align-items: center; gap: 10px;">
        <input type="checkbox"  @click="toggleTagOnCheckbox">

        <component :is="CurrentTag" ref="text"id="text" @click="setEditingState" @focusout="removeEditingState"><slot></slot></component>
        
        <VButton>delete</VButton>
    </div>
</template>
<script>
export default {
    props:{

    },
    data(){
        return{
            CurrentTag:'p',
            PreviousTag:'',
            IsEditing:false
        }
    },
    methods:{
        test(){
            console.log("helo")
        },
        toggleTagOnCheckbox(){
            this.CurrentTag = this.CurrentTag === 'p' ? 'del' : 'p'
            console.log(this.PreviousTag + '1')
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