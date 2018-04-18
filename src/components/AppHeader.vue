<template>
  <nav>
    <ul id="menu">
      <li class="right" v-if="loggedIn">
        <a class="logBut" @click="logout" href="#">Logout</a></p>
      </li>
      <li class="right" v-else>
       <form v-on:submit.prevent="login">
         Have an Account? Log in Now.
         <input class="field" v-model="email" placeholder="Email Address">
         <input class="field" v-model="password" type="password" placeholder="Password">
         <button class="login" type="submit">LOGIN</button>
       </form>
      </li>
    </ul>
    <div class="flexWrapper errorPlace">
      <p v-if="loginError" class="flexRight error">{{loginError}}</p>
    </div>
  </nav>
</template>

<script>
 export default {
   name: 'AppHeader',
   data () {
     return {
        keywords: '',
       email: '',
       password: '',
     }
   },
   computed: {
     user: function() {
       return this.$store.getters.user;
     },
     loggedIn: function() {
       return this.$store.getters.loggedIn;
     },
     loginError: function() {
       return this.$store.getters.loginError;
     },
   },
   methods: {
     search: function() {
       this.$router.push({ path: '/search', query: { keywords: this.keywords }})
       this.keywords = '';
     },
     login: function() {
       this.$store.dispatch('login',{
         email: this.email,
         password: this.password,
       }).then(user => {
	 this.email = '';
	 this.password = '';
       });
     },
     logout: function() {
       this.$store.dispatch('logout');
     }
   }
 }
</script>
<style scoped>
 /* Strip the ul of padding and list styling */
 nav {
     display: grid;
     margin-bottom: 20px;
 }
 ul {
     list-style-type:none;
     margin:0;
     padding:0;
     margin-top: 10px;
 }
 /* Create a horizontal list with spacing */
 li {
     display:inline-block;
     float: left;
     margin-right: 20px;
     text-align: center;
     color: #666;
 }
 .logBut{
     color: white;
     background-color: teal;
     padding: 8px;
     text-decoration: none;
 }
 /*Active color*/
 li a.active {
 }
 /*Hover state for top level links*/
 li:hover a {
 }
 .right {
     float: right;
 }
 .errorPlace {
     height: 20px;
 }
 input {
     height: 0.5em;
 }
 .search {
     margin-left: 5px;
 }
 .field{
     border: 2px solid teal;
     padding: 10px;
     font-size: 16px;
 }
 .login{
     background-color: teal;
     color: white;
     font-size: 15px;
     margin-bottom: 0px;
     padding: 8px;
 }
</style>
