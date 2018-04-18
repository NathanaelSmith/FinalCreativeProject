<template>
  <div class="column">
  <div class ="register">
    <h2>Sign up today. It's free.</h2>
    <form v-on:submit.prevent="register">
      <h2>Create An Account Now.</h2>
      <input class="wide" v-model="username" placeholder="User Name"><br/>
      <input class="wide" v-model="name" placeholder="First and Last Name"><br/>
      <input class="wide" v-model="email" placeholder="Email Address"><br/>
      <input class="wide" type="password" v-model="password" placeholder="Password"><br/>
      <button class="makeButton" type="submit">CREATE ACCOUNT</button>
    </form>
    <p class="error">{{registerError}}</p>
  </div>
  <div class="advertise">
    <h1>MyNotes</h1>
    <ul>
	<li>Take Notes, whenever, wherever, however</li>
	<li>Create, delete, and edit your notes in one secure place</li>
	<li>Get smarter in class as you take notes with MyNotes</li>
        <li>Never miss a beat with MyNote</li>
    </ul>
    <h2>Remember its FREE and always will be!</h2>
  </div>
  </div>
</template>
<script>
 export default {
   name: 'WelcomePage',
   data () {
     return {
       username: '',
       email: '',
       password: '',
       name: '',
     }
   },
   computed: {
     registerError: function() {
       return this.$store.getters.registerError;
     },
   },
   methods: {
     register: function() {
       this.$store.dispatch('register',{
	 username: this.username,
         email: this.email,
         password: this.password,
	 name: this.name,
       });
     }
   }
 }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 h1 {
     margin-bottom: 0px;
     color: teal;
     text-align: center;
 }
 h2 {
     margin-top: 0px;
     font-size: 1.2em;
     font-weight: normal;
     margin-bottom: 2px;
     text-align: center;
 }
 .wide {
     width: 370px;
     border: 2px solid teal;
     padding: 5px;
     font-size: 17px;
     color: black;
     margin-top: 3px;
 }
 .makeButton{
     width: 370px;
     font-size: 16px;
     color: white;
     margin-top: 7px;
     margin-bottom: none;
     text-align: center;
     background-color: Teal;
 }
 .register {
     padding: 5px;
     width: 45%;
     margin-left: 10px;
     background-color: white;
     height: 360px;
     float: left;
     text-align: center;
 }
 .advertise{
    padding: 5px;
    margin-right: 10px;
    width: 45%;
    background-color: white;
    height: 360px;
    float: right;
 }
 .advertise li{
   font-size: 16px;
   margin-bottom: 4px;
  }
  .advertise h2{
   fontsize: 20px;
  }
 .column{
    margin-top: 10px;
 }

</style>
