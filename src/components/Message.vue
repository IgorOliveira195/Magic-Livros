<template>
    <div class="message">
        <p>{{msg}}</p>
    </div>
</template>
<script>
export default {
    name: "Message",

    props:{
        msg: String
    }  
}
</script>

<style scoped>
    .message{
        color: #4d4bd6;
        background-color: #5be9c5;
        border: 2px solid #b8daff;
        border-radius: 10px;
        padding: 15px;
        text-align: center;
        font-size: 20px;
        max-width: 400px;
        margin: 30px auto;
    }
</style>
