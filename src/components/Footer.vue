<template>
    <div class="footer">
        <p>Copyrigth &copy; 2022 Igor Oliveira Holanda - Todos os Direitos Reservados</p>
    </div>
</template>

<script>
export default {
    name: 'Footer'
    
}
</script>

<style scoped>

    hr{
        border-color: rgba(209, 209, 209, 0.678);
    }
    .footer{
        background-color: #2f5dab;
        border-top: 5px solid #FFB02E;
        display: flex;
        align-items: center;
        justify-content: center;
        height: 175px;
        width: 100%;
    }

    p{
        color: #fff;
        font-size: 20px;
    }
</style>