<template>
  <div class="container">
    <h1>Novo usuário</h1>
    <form @submit.prevent="enviarFormulario">
      <div class="form-group">
        <label for="nome">Nome</label>
        <input type="text" class="form-control" v-model="usuario.nome" />
      </div>
      <div class="form-group">
        <label for="email">E-mail</label>
        <input type="email" class="form-control" v-model="usuario.email" />
      </div>
      <div class="form-group">
        <label for="senha">Senha</label>
        <input type="password" class="form-control" v-model="usuario.senha" />
      </div>
      <p class="alert alert-danger" v-if="mensagemErro">{{ mensagemErro }}</p>
      <button class="btn btn-primary" type="submit">Salvar</button>
    </form>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      usuario: {
        nome: "",
        senha: "",
        email: "",
      },
      mensagemErro: "",
    };
  },
  methods: {
    enviarFormulario() {
      this.$http
        .post("auth/register", this.usuario)
        .then(() => {
          this.$router.push({ name: "login" });
          this.ensagemErro = "";
        })

        .catch((erro) => {
          if (erro.request.status === 401) {
            this.mensagemErro = "Usuario ja existe";
          }
        });
    },
  },
};
</script>
