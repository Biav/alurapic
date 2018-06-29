
let template = `<template>
  <div id="app" class="corpo">
    <img src="./assets/logo.png">
    <h1 class="centralizado">{{ msg }}</h1>
    <h2>Essential test</h2>
    <ul class="lista-fotos">
      <li class="lista-fotos-item" v-for="foto in fotos">
      <meu-painel :titulo="foto.titulo">
        <img class="imagem-responsiva" :src="foto.url" :alt="foto.titulo">
      </meu-painel>
    </li>
    </ul>
  </div>
</template> `;

<script>
import Painel from './components/shared/painel/Painel.vue';

export default {
  name:'app',
  components: {
    'meu-painel': Painel
  },
  data () {
    return {
      msg: 'Vue.js App',
      fotos: []
    }
  },
  created(){
    this.$http.get('http://localhost:3000/v1/fotos')
    .then(res => res.json())
    .then(fotos => this.fotos = fotos, err => console.log(err));
  }
}
</script>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.centralizado {
    text-align: center;
  }

.corpo {
  font-family: Helvetica, sans-serif;
  margin: 0 auto;
  width: 96%;
}

.imagem-responsiva {
  width: 100%;
}

.lista-fotos {
  list-style: none;
}

.lista-fotos .lista-fotos-item {
  display: inline-block;
}

.painel {
  padding: 0 auto;
  border: solid 2px grey;
  display: inline-block;
  margin: 5px;
  box-shadow: 5px 5px 10px grey;
  width: 200px;
  height: 100%;
  vertical-align: top;
  text-align: center;
}

.painel .painel-titulo {
  text-align: center;
  border: solid 2px;
  background: lightblue;
  margin: 0 0 15px 0;
  padding: 10px;
  text-transform: uppercase;
}
</style>
