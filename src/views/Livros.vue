<template>
  <div class="livros">
    <div class="campoPesquisa">
      <input type="text" v-model="search" placeholder="O que está buscando ?" />
    </div>
    <div class="campo-livros">
        <div class="livros-cadastrados" v-for="livro in filteredLivro" :key="livro.id" v-if="filteredLivro.length >0">
            <button class="delete-button" @click="deleteLivros(livro.id)"><i class="gg-close-r"></i></button>
            <button class="status-button-disponivel">Disponível</button>
          <div class="nome-livro">{{livro.nome}}</div>
          <div class="autor-livro"><span>por: </span>{{livro.autor}}</div>
          <div class="descricao-livro">{{livro.descricao}}</div>
        </div>
        <div class="campo-vazio" v-else>
          <h1>Nenhum livro encontrado ou adicionado</h1>
        </div>
      </div>
  </div>
</template>

<script>

export default {
  name: 'Livros',
  data(){
    return{
      novosLivros: [],
      search: ""
    }
  },

  methods: {
    async getLivros(){
      const req = await fetch("http://localhost:3000/novosLivros");
      const data = await req.json();
      this.novosLivros  = data;
    },

    async deleteLivros(id){
      const req =await fetch(`http://localhost:3000/novosLivros/${id}`,{
        method: "DELETE"
      });

      const res = await req.json();
      this.getLivros();
    },
  },

  computed: {
    filteredLivro(){
      return this.novosLivros.filter((livro) =>{
      return livro.nome.toUpperCase().indexOf(this.search.toUpperCase()) > - 1;
      });   
    }
  },

  mounted(){
    this.getLivros();
  }
}
</script>

<style scoped>

  @import url('https://css.gg/close-r.css');

  .livros{
    margin-left: 50px;
    margin-top: 50px;
    margin-bottom: 14%;
    min-height: 500px;
  }

  .campoPesquisa{
    margin-bottom: 20px;
  }

  input{
    background-image: url("https://media.istockphoto.com/vectors/magnifying-glass-graphic-icon-design-template-vector-id1086362956?k=20&m=1086362956&s=170667a&w=0&h=mPIeIWsKb1ZCo9WFl88WCAEngt1GKJ-wnjGzm_b6pm8=");
    background-repeat: no-repeat;
    background-position: left;
    background-size: 35px;
    padding: 10px 15px 10px 40px;
    width: 250px;
    border-radius: 10px;
    border: 2px solid #FFB02E;
  }

  .campo-livros{
      display: flex;
      flex-flow: row wrap;
      margin: 50px auto;
  }

  .livros-cadastrados{
    background-color: #FFFFFF;
    width: 330px;
    height: 400px;
    border-radius: 10px;
    border: 3px solid #FFB02E;
    padding: 15px;
    margin: 0 15px 15px 0;
  }

  .nome-livro{
    font-size: 25px;
    font-weight: bold;
    word-break: break-all;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    max-width: 300px;
    max-height: 55px;  
    margin-bottom: 10px;    
   -webkit-line-clamp: 2; 
   -webkit-box-orient: vertical;
    
  }

  .delete-button{
    position: absolute;
    margin: 5px 0 0 310px;
    width: 20px;
  }

  .delete-button:hover{
    cursor: pointer;
  }

   .delete-button:active{
    opacity: 0.5;
  }

  .gg-close-r{
    background-color: #dd4646;
    color: #fff;
  }

  .autor-livro{
    color: #3dd15d;
    font-weight: bold;
    margin-bottom: 15px;
  }

  span{
    color: rgb(46, 46, 46);
  }

  .descricao-livro{
    color: rgb(102, 100, 100);
    word-break: break-all;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    line-height: 20px;     /* fallback */
    max-height: 120px;      /* fallback */
   -webkit-line-clamp: 6; /* number of lines to show */
   -webkit-box-orient: vertical;
  }

  .status-button-disponivel{
    background-color: #3dd15d;
    border-radius: 15px;
    font-size: 20px;
    color: #fff;
    font-weight: bold;
    margin: 350px 17px;
    font-size: 20px;
    padding: 15px 100px;
    position: absolute;
  }

  .status-button-disponivel:hover{
    background-color:  #FFB02E;
    cursor: pointer;
  }

  .status-button-disponivel:active{
    opacity: 0.5;
  }

  .campo-vazio{
    display: flex;
    margin: 150px auto;
  }

  h1{
    background-color: #fff;
    padding: 10px 20px;
    border-radius: 15px;
    color: #FFB02E;
    font-size: 50px;
    font-weight: bold;
  }

</style>
