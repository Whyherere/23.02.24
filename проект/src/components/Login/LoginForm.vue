<template>
    <v-sheet width="300" class="mx-auto">
      <v-form @submit.prevent>
        <v-text-field
          v-model="login"
          :rules="rulesLogin"
          label="Логин"
        />
        <div>
          <div v-if="errorsLogin.length">
            <span v-for="error in errorsLogin" class="errors">{{ error }}</span>
          </div>
        </div>
        <v-text-field
          type="password"
          v-model="password"
          :rules="rulesPass"
          label="Пароль"
          class="input"
        />
        <div>
          <div v-if="errorsPassword.length">
            <span v-for="error in errorsPassword" class="errors">{{ error }}</span>
          </div>
        </div>
        <v-btn @click="check" type="submit" block class="mt-2">Войти</v-btn>
      </v-form>
    </v-sheet>
  </template>
  
  <script>
  
  
  export default {
    name: 'LoginForm',
  
    components: {
      
    },
  
    data: () => ({
      login: '',
      password: '',
      errorsLogin: [],
      errorsPassword: [],
      
    }),
    methods: {
        check(){
          this.errorsPassword = [];
          this.errorsLogin = [];
          if (this.password.length < 6) {
            this.errorsPassword.push('Пароль должеть быть больше 6 символов');
          }
          if (this.login.length < 5) {
            this.errorsLogin.push('Логин должеть быть больше 6 символов');
          }
          const userData = {
            login: this.login,
            password: this.password,
          }
          this.$store.commit('LOGIN', userData)

          if (this.$store.state.user.curUser != ''){
            this.$router.push('/')
          }
        }
      }
    }
  </script>
  <style>
    .errors {
      color:  rgb(0, 0, 0);
    }
  </style>