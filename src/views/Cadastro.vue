<template>
<ErrorMessage :error="error" v-show="error"/>
<Message :msg="msg" v-show="msg"/>
    <div class="cadastro">
        <form class="dados" @submit="createLivros">
          <p>Adicionar novo livro</p>
          <h5>Nome:</h5>
          <input type="text" name="nome" placeholder="Ex: Desenvolvimento NodeJS"  id="nome" v-model="nome"/>
          <h5>Autor:</h5>
          <input type="text" name="autor" placeholder="Ex: José Monteiro Valasques" id="autor" v-model="autor"/>
          <h5>Descrição:</h5>
          <input type="text" name="descricao" placeholder="Ex: Este livro explica o desenvolvimento desde..." id="descricao" v-model="descricao"/>
          <input type="submit" value="Cadastrar" class="button">
        </form>
    </div>
</template>

<script>
import Message from "../components/Message.vue"
import ErrorMessage from "../components/ErrorMessage.vue"

export default {
  name: 'Cadastro',

  components:{
    Message,
    ErrorMessage
},

  data(){
    return{
      nome: "",
      descricao: "",
      autor: "",
      msg: "",
      error: ""
    }
  },

  methods: {
    async createLivros(e){
      e.preventDefault();

      const data = {
        nome: this.nome,
        descricao: this.descricao,
        autor: this.autor
      }

      if(this.nome == "" || this.descricao == "" ||  this.autor == ""){
         this.error = "Por favor, preencha todos os campos";
         setTimeout(()=> this.error = "",2000);
      }

      else{
        const dataJson = JSON.stringify(data);
        const req = await fetch("http://localhost:3000/novosLivros", {
          method: "POST",
          headers: {"Content-Type": "application/json"},
          body: dataJson
        });
        const res = await req.json();
        
        this.msg = `O livro ${res.nome} foi cadastrado com sucesso !!!`;
        setTimeout(()=> this.msg = "",2000);     
      }

      this.nome = "";
      this.descricao = "";
      this.autor = "";
    }
  }
}
</script>

<style scoped>

  .cadastro{
    margin: auto;
    margin-bottom: 100px;
    min-height: 858px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .dados{
      background-color: #fff;
      width: 500px;
      height: 500px;
      padding: 20px;
      border-radius: 20px;
      position: relative;
      border: 3px solid #FFB02E;
  }

  p{
    font-size: 30px;
    font-weight: bold;
    margin-bottom: 50px;
    text-align: center;
  }

  h5{
    font-size: 16px;
  }

  input{
    width: 470px;
    padding: 15px;
    border: 1px solid;
    border-radius: 10px;
    margin-bottom: 20px;
    border: 1px solid #e2e2e2;
  }

  .button{
    background-color: #3dd15d;
    border-radius: 15px;
    font-size: 20px;
    color: #fff;
    font-weight: bold;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    margin-top: 160px;
  }

  .button:hover{
    background-color:  #FFB02E;
    cursor: pointer;
  }

  .button:active{
    opacity: 0.5;
  }



</style>
