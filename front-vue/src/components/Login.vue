<template>

  <div class="centered-container">

    <md-content class="md-elevation-8">
      <div class="title">
        <img src="/static/images/aluno.png" />
        <div class="md-title">ÁREA DO ALUNO</div>
        <div class="md-body-1">Login</div>
      </div>
      <p v-if="$route.query.redirect">
          You need to login first.
      </p>
      <div class="form">
      <form @submit.prevent="login" autocomplete="off">
        <md-field>
          <label>E-mail</label>
          <md-input v-model="login.email" autofocus></md-input>
        </md-field>
        <md-field md-has-password>
          <label>Senha</label>
          <md-input v-model="login.password" type="password"></md-input>
        </md-field>
        </form>
      </div>
      <div class="actions md-layout md-alignment-center-space-between">
        <a href="/resetpassword">Recuperar Senha</a>
        <router-link v-bind:to="{ name: 'Home' }" class="">
        <md-button class="md-raised md-primary" @click="auth">Log in</md-button>
        </router-link>
      </div>
      <div class="loading-overlay" v-if="loading">
        <md-progress-spinner md-mode="indeterminate" :md-stroke="2"></md-progress-spinner>
      </div>
    </md-content>

    <md-content class=" md-elevation-8">
      <div class="title">
        <img src="/static/images/adm.png" />
        <div class="md-title">ÁREA DO COORDENADOR</div>
        <div class="md-body-1">Login</div>
      </div>
      <p v-if="$route.query.redirect">
          You need to login first.
      </p>
      <div class="form">
      <form @submit.prevent="login" autocomplete="off">
        <md-field>
          <label>E-mail</label>
          <md-input v-model="login.email" autofocus></md-input>
        </md-field>
        <md-field md-has-password>
          <label>Senha</label>
          <md-input v-model="login.password" type="password"></md-input>
        </md-field>
        </form>
      </div>
      <div class="actions md-layout md-alignment-center-space-between">
        <a href="/resetpassword">Recuperar Senha</a>
        <router-link v-bind:to="{ name: 'Home' }" class="">
        <md-button class="md-raised md-primary" @click="auth">Log in</md-button>
        </router-link>
      </div>
      <div class="loading-overlay" v-if="loading">
        <md-progress-spinner md-mode="indeterminate" :md-stroke="2"></md-progress-spinner>
      </div>
    </md-content>



    <div class="background" />

  </div>

</template>




<script>
import HoursService from '@/services/HoursService'
export default {
  name: "App",
  data() {
    return {
      loading: false,
      login: {
        email: "",
        password: ""
      }
    };
  },

  methods: {
    auth() {
      // your code to login user
      // this is only for example of loading
      this.loading = true;
      setTimeout(() => {
        this.loading = false;
      }, 5000);
    }
  }
};
</script>

<style lang="scss">
.centered-container {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  height: 100vh;
  .title {
    text-align: center;
    margin-bottom: 30px;
    img {
      margin-bottom: 16px;
      max-width: 200px;
    }
  }
  .actions {
    .md-button {
      margin: 0;
    }
  }
  .form {
    margin-bottom: 60px;

  }
  .background {
    position: absolute;
    height: 100%;
    width: 100%;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    z-index: 0;
    background-color: #4682B4;
  }
  .md-content {
    z-index: 1;
    padding: 40px;
    width: 100%;
    max-width: 400px;
    position: relative;
    margin-right: 8%;
    margin-left: 8%;
  }
  .loading-overlay {
    z-index: 10;
    top: 0;
    left: 0;
    right: 0;
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.9);
    display: flex;
    align-items: center;
    justify-content: center;
  }
}



</style>
