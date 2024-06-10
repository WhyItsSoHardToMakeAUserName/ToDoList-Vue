<template>
    <button :style>
        <slot></slot>
    </button>
</template>
<script>
export default {
    props:{
        style:Object,
    }
}
</script>
<style scoped>
    button{
        border: none;
        border-radius: 25px;

        padding: 7px 20px;
        
        color: white;

        background-color: #647bfa;
        transition: all 0.3s
    }
    button:hover{
        background-color: #435ffd;
        transition: all 0.3s
    }
</style> 
