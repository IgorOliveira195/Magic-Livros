<template>
    <nav>
        <div class="logo">   
            <img src="../assets/logo.png" alt="Magic Livros"/>
        </div>
        <router-link to="/">Home</router-link> 
        <router-link to="/livros">Livros</router-link>
        <router-link to="/cadastro">Cadastro</router-link>
    </nav>
</template>

<script>
export default{
    name: 'Navbar'
}
</script>

<style scoped>
    nav{
        border-bottom: 5px solid #FFB02E;
        background-color: #2f5dab;
        display: flex;
        align-items: center;
        padding: 15px 50px;
        justify-content: flex-end;
    }

    nav a{
        color: #fff;
        text-decoration: none;
        margin: 15px;
        font-size: 35px;
        font-weight: bold;
    }

     nav a:hover{
        color: #FFB02E;
        border-bottom: 3px solid #FFB02E ;
    }

    nav a:active{
        color: #fff;
    }
    .logo{
        margin: auto;
        margin-left: 0;
    }

    img{
        width: 250px;
        height: 120px;
    }
</style>
