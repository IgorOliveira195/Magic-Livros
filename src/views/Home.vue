<template>
  <div class="home">
      <p class="title">Seja bem vindo ao <span class="livros-text">Livros </span><span class="magic-text">Magic!</span></p>
      <p>O maior Catálogo de livros da Zona Franca de Manaus</p>
      <router-link to="/livros">
        <button>Ver Catálogo</button>
      </router-link>
  </div>
</template>

<script>


export default {
  name: 'Home',

}
</script>

<style scoped>

  .home{
    margin-top: 100px;
    margin-bottom: 14%;
    min-height: 500px;
    justify-content: center;
    position: relative;
  }

  .home a{
    text-decoration: none;
  }

  .livros-text{
    color: #FFB02E;
  }
  .magic-text{
    color: #fff;
  }

  .title{
    color: #3dd15d;
    font-size: 100px; 
    font-weight: bold;
    text-align: center;
  }

  p{
    text-align: center;
    font-size: 50px;
    color: #fff;
    margin-bottom: 20px;
  }

  button{
    background-color: #fff;
    border: 3px solid #3dd15d;
    border-radius: 15px;
    padding: 15px 50px;
    font-size: 30px;
    color: #3dd15d;
    font-weight: bold;
    margin: 100px auto;
    display: flex;
  }

  button:hover{
    border: 3px solid #FFB02E;
    color: #FFB02E;
    cursor: pointer;
  }

  button:active{
    opacity: 0.5;
  }

 
</style>
