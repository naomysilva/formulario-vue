<template>
	<div id="app">
		<h1>Formulário Desafio</h1>
		<div class="conteudo">
			<form class="painel"v-if="!enviado" >
				<div class="cabecalho" >Formulário</div>
				<div class="form" >
					<Rotulo nome="Nome completo" >
						<input v-model="user.nomeCompleto" type="text">
					</Rotulo>
					<Rotulo nome="Email">
						<input v-model="user.email" type="email">
					</Rotulo>
					<Rotulo nome="Senha">
						<input v-model="user.senha" type="password">
					</Rotulo>
					<Rotulo nome="Armazenar Dados">
						<span><input type="radio" value="Sim" v-model="escolha">Sim</span>
						<span><input type="radio" value="nao" v-model="escolha">Não</span>
					</Rotulo>
				</div>
				<button @click.prevent="enviar">Enviar</button>
			</form>
			<div class="painel" v-else >
				<div class="cabecalho">Resultado</div>
					<Rotulo>
						<span>{{ user.nomeCompleto }}</span>
					</Rotulo>
					<Rotulo>
						<span>{{ user.email }}</span>
					</Rotulo>
					<Rotulo>
						<span>{{ user.senha }}</span>
					</Rotulo>
					<Rotulo>
						<span>{{ escolha }}</span>
					</Rotulo>
			</div>
		</div>
	</div>
</template>

<script>
import Rotulo from "./components/Rotulo.vue";

export default {
  name: "app",
  components: { Rotulo },
  data() {
    return {
      escolha: "sim",
      enviado: false,
      user: {
        nomeCompleto: "",
        email: "",
        senha: "",
      },
    };
  },
  methods: {
    enviar() {
      this.enviado = true;
    },
  },
};
</script>

<style>
body {
  background-color: #ececec;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  display: flex;
  flex-direction: column;
}

.conteudo {
  display: flex;
}

.painel {
  flex: 1;
  background: #fff;
  margin: 0px 10px;
  padding: 20px;
  border: 1px solid #aaa;
  border-radius: 5px;
}

.painel .cabecalho {
  width: 100%;
  background-color: #ddd;
  padding: 10px 0px;
  border-radius: 5px;
  font-size: 1.4rem;
}

#app form button {
  float: right;
  margin: 10px 0px;
  padding: 10px 20px;
  font-size: 1.4rem;
  border-radius: 5px;
  color: #fff;
  background-color: #2196f3;
}

#app h1 {
  font-weight: 200;
  margin: 20px;
  padding: 0;
}

.mr-4 {
  margin-right: 40px;
}
</style>
