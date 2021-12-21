<template>
  <div id="app">
    <h1>Fazer Cadastro</h1>

    <div>
      <form @submit="enviar">
        <label>Nome </label>
        <input type="text" v-model="user.nome" />

        <label>Email </label>
        <input type="email" v-model="user.email" />

        <label>Qtd de funcionários </label>
        <input type="number" v-model="user.qtdFunc" />

        <label>Opinião </label>
        <textarea v-model="opiniao" cols="30" rows="10"></textarea>
        
        <label>Tecnologias </label>
        <span><input type="checkbox" value="javascript" v-model="tecnologias"/>Javascript</span>
        <span><input type="checkbox" value="CSS" v-model="tecnologias"/>CSS</span>
        <span><input type="checkbox" value="Vue.js" v-model="tecnologias"/>Vue.js</span><br/>

        <label>Tipo de contratação </label>
        <select v-model="tipoSelecionado">
          <option v-for="item in tipos" :key="item.id" :value="item.nome">{{item.nome}}</option>
        </select><br/>

        <label>Qual seu nível? </label>
        <span><input type="radio" value="basico" v-model="nivel"/>Básico</span>
        <span><input type="radio" value="intermediario" v-model="nivel"/>Intermediário</span>
        <span><input type="radio" value="avancado" v-model="nivel"/>Avançado</span>

        <button type="submit">Enviar</button>

      </form>
    </div>

    <hr />

    <div class="item" v-show="resultado">
      <h2>Usuário cadastrado</h2>
      <label>Nome: {{ user.nome }}</label><br />
      <label>Email: {{ user.email }}</label><br />
      <label>Quantidade de funcionários: {{ user.qtdFunc }}</label><br/>
      <label>Opinião: <br/>{{opiniao}}</label><br/>
      <label>Tecnologias:</label>
      <ul>
        <li v-for="tech in tecnologias" :key="tech">{{tech}}</li>
      </ul><br/>
      <label>Tipo de contratação: {{tipoSelecionado}}</label><br/>
      <label>Nivel atual: {{nivel}}</label>
    </div>

  </div>
  </template>

<script>
export default {
  name: "App",
  data() {
    return {
      user: {
        nome: "",
        email: "",
        qtdFunc: 0,
      },
      opiniao: '',
      tecnologias: [],
      tipos:[
        {id: 1, nome: 'Freelancer'},
        {id: 2, nome: 'CLT'},
        {id: 3, nome: 'PJ'},
        {id: 4, nome: 'Remoto'}
      ],
      tipoSelecionado: 'Freelancer',
      nivel: 'basico',
      resultado: false
    };
  },
  methods:{
    enviar(e){
      e.preventDefault();
      alert("Cadastrado com sucesso!");
      this.resultado = true;
    }
  }
  
};
</script>

<style scoped>
  form{
    display: flex;
    flex-direction: column;
    max-width: 300px;
  }
</style>
