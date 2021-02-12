<template>
    <div>
        <img src="../assets/logo.png" alt="Vue logo">
        <p>{{ bienvenue || "Bienvenue !"}}  sur mon site</p>
        <button @click="sendBounce"> Bounces with parent  : {{ bounces }} </button>
    </div>
</template>
<script>
export default {
    name:"Logo",
    props:["bienvenue","bounces"],
    data(){
        return {
            real:true,
        }
    },
    methods:{
        sendBounce(){
            this.$emit('sendBounce');
        }
    }
}
</script>
<style scoped>
    img{
        height:200px;
    }
</style>