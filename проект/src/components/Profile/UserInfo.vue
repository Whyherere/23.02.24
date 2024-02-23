<template>
    <v-app>
      <v-main>
        <div>
          <div v-if="this.user != ''">
            <img class="img" src="https://www.unadornedjewelrydesign.com/wp-content/uploads/2018/11/account.png">
            <p>Имя: {{ this.user.fullname }}</p>
            <p>Логин: {{ this.user.login }}</p>
            <p>e-mail: {{ this.user.email }}</p>
            <p>роль: {{ this.user.role }}</p>
            
           <div class="btn"> <button @click="Out">Выйти с аккаунта</button></div>
          </div>
          <p v-else>Вы не зашли на аккаунт</p>

        </div>
        </v-main>
    </v-app>
  </template>
  
  <script>
  
  
  export default {
    name: 'UserInfo',
  
    components: {
      
    },
  
    data: () => ({
      //
    }),
    methods: {
      Out(){
        if (this.$store.state.user.curUser != ''){
          this.$store.state.user.curUser = ''
          alert('Вы вышли из аккаунта')
        }
      }
    },
    computed: {
      user(){
        return this.$store.state.user.curUser
      }
    }
  }
  </script>
  
<style>
  .img{
    height: 100px;
    width: 100px;
  }
 .btn{
 border: 1px solid rgb(0, 0, 0);
    margin: auto;
    width: 150px;

  
 }



</style>