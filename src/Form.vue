<template>
  <div class="fullScreen">
    <div id="main">
      <div class="card">
        <div class="card-body">
          <h5 class="card-title">Cadastro de Usuários</h5>
          <p class="card-text">Preencha os campos abaixo para cadastrar um usuário.</p>
          <div class="row mt-4 justify-content-center">
            <div class="col-12 mt-4">
              <float-label>
                <input type="text" class="form-control" v-model="nome" placeholder="Nome" />
              </float-label>
            </div>
          </div>
          <div class="row mt-4 justify-content-center">
            <div class="col-12 mt-4">
              <float-label>
                <input type="text" class="form-control" v-model="email" placeholder="E-mail" />
              </float-label>
            </div>
          </div>
          <div class="row mt-4 justify-content-center">
            <div class="col-12 mt-4">
              <float-label>
                <input type="password" class="form-control" v-model="senha" placeholder="Senha" />
              </float-label>
            </div>
          </div>
          <div class="row mt-4 justify-content-center">
            <button class="btn btn-md btn-outline-primary" @click="cadastrarUsuario">Cadastrar</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FloatLabel from "vue-float-label/components/FloatLabel";

export default {
  components: {
    FloatLabel
  },
  data() {
    return {
      nome: "",
      email: "",
      senha: ""
    };
  },
  methods: {
    cadastrarUsuario() {
      var clientSocket = new WebSocket("ws://localhost:2000/");

      var data = {
        nome: this.nome,
        email: this.email,
        senha: this.senha
      };

      clientSocket.onopen = () => {
        clientSocket.send(JSON.stringify(data));
      };

      clientSocket.onmessage = message => {
        console.log(message);
      };
    }
  }
};
</script>

<style>
#main {
  position: absolute;
  top: 25%;
  left: 37.5vw;
  min-height: 50%;
  min-width: 25vw;
}

.fullScreen {
  min-height: 100vh !important;
  min-width: 100vw !important;
  background-size: cover;
  background-position: center;
  background-image: url("./assets/fundoResetar.jpg");
}

input {
  outline: none !important;
  -webkit-box-shadow: none !important;
  -moz-box-shadow: none !important;
  box-shadow: none !important;
}
</style>