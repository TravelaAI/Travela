<template>
    <div class="mt-15">
      <v-row class="page d-flex justify-center align-center" color="">
        <v-col cols="12" md="4" class="pa-2 ps-4">
          <v-card elevation="2" class="d-flex flex-column pa-4 grey lighten-2">
           <h1 class="text-center mt-2 mb-2 logInFont   font-weight-bold">TRAVELA</h1>
       
            <v-text-field name="email" id="email" v-model="email" v-model.lazy="email" outlined label="Email Address"
                          autocomplete="off"  class="mb-3 custom-text-field" hide-details>
              <template v-slot:prepend-inner>
                <i class="mgc_mail_fill prepend-icon-size grey--text"></i>
              </template>
            </v-text-field>
            <v-text-field id="password" name="password" label="Password" outlined v-model="password"
                          class="mb-4 custom-text-field" hide-details>
            </v-text-field>
            <div class="d-flex">
              <router-link class="forgot" align="start" to="/forgot">Forgot password?</router-link>
    
            </div>
            <div class="d-flex">
              <v-btn class="mt-12 login-btns yellow darken-3" block depressed width="73%" 
                     @click="loginMethod()">
                Login
              </v-btn>
            </div>
          </v-card>
        </v-col>
      </v-row>

    </div>
  </template>
  
  <script>
  import axios from "axios";
//   import config from "@/configuration/config";
  
  export default {
    name: "LoginPage",
  
    data: () => ({
      email: "",
      showpass: false,
      password: "",

    }),
    methods: {
      ClearStorage() {
        this.$store.state.isLoggedIn = false,
            localStorage.removeItem('isLoggedin');
      },
      async loginMethod() {

        axios
        .post('http://127.0.0.1:5000/api/auth/login', {
          username: this.username,
          password: this.password,
        })
        .then(response => {
          // Handle successful login
          console.log(response.data)
          const token = response.data.token;
          // Save the token in local storage or Vuex store for further use
          localStorage.setItem('token', token);
          // Redirect to another page or perform any other actions
        })
        .catch(error => {
          // Handle login error
          console.error('Login failed:', error);
        });
      },

    },
    created() {
      this.ClearStorage();
    }
  }
  </script>
  <style scoped>
  * {
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  }
  .eye-icon{
    font-size: 22px !important;
    cursor: pointer;
  }
  
  /* Change Autocomplete styles in Chrome*/
  input:-webkit-autofill,
  input:-webkit-autofill:hover,
  input:-webkit-autofill:focus,
  textarea:-webkit-autofill,
  textarea:-webkit-autofill:hover,
  textarea:-webkit-autofill:focus,
  select:-webkit-autofill,
  select:-webkit-autofill:hover,
  select:-webkit-autofill:focus {
    -webkit-box-shadow: none;
    -webkit-background-clip: text;
    transition: background-color 5000s ease-in-out 0s;
  }
  
  .v-progress-circular {
    position: absolute;
    top: calc(50% - 100px);
    left: calc(50% - 25px);
  }
  
  .v-dialog {
    position: absolute;
    top: calc(50% - 50px);
    left: calc(50% - 150px);
  }
  
  .v-application a {
    margin-left: 0px;
    text-decoration: none;
    text-transform: initial;
    font-weight: 500;
    font-size: 13px;
  }
  .logInFont{
  font-family:Roboto,sans-serif !important;  
   font-size: 24px !important;
   color:#64718A !important;
   ;
}
  </style>