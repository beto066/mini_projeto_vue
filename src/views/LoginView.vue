<script setup>

</script>

<template>
  <div>
      <form @submit.prevent="login">
        <table>
          <thead><h1 class="text-center" >Login</h1></thead>
          <tr>
            <td><label class="text-azul b" for="username">Email: </label></td>
            <td><input type="email" id="username" v-model="user.email" required/></td>
          </tr>
          <tr>
            <td><label class="text-azul b" for="password">Senha: </label></td>
            <td><input type="password" id="password" v-model="user.password" required/></td>
          </tr>
        </table>
      </form>
        <input class="button text-center" @click="salvar" type="submit" value="Login" />  
    </div>
</template>

<script type="module">
  import axios from 'axios';

  export default {
    el: '#app',
    data(){
      return {
        user : {
          password : '',
          email : ''
        },

        async salvar(){
          axios.post('http://127.0.0.1:8000/api/login', this.user).then(({ data }) => {
            localStorage.token = data.remember_token;
          
            console.log(data.remember_token);
          });
        }
      }
    },
    mounted (){
    }
  }
</script>
