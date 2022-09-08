<template>
    <div class="error">
        <p>{{error}}</p>
    </div>
</template>
<script>
export default {
    name: "ErrorMessage",

    props:{
        error: String
    }  
}
</script>

<style scoped>

    .error{
        color: #ffffff;
        background-color: #ff0000;
        border: 2px solid #b8daff;
        border-radius: 10px;
        padding: 15px;
        text-align: center;
        font-size: 20px;
        max-width: 400px;
        margin: 30px auto;
    }
</style>
