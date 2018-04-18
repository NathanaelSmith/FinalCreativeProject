<template>
  <div id="app">
    <div class="myHeader">
       <app-header/>
    </div>
    <router-view/>
    <div class="footer">
    <a href="https://github.com/NathanaelSmith/FinalCreativeProject">GitHub</a>
    </div>
  </div>
</template>

<script>
 import AppHeader from './components/AppHeader';
 export default {
   name: 'App',
   components: { AppHeader }
 }
</script>

<style>
 /* https://color.adobe.com/CS04-color-theme-1994456/?showPublished=true */
 body {
     margin: 0px;
     padding: 0px;
     font-size: 18px;
     font-family: 'Avenir', Helvetica, Arial, sans-serif;
     background-color: palegreen;
 }
 button {
     color: #fff;
     min-width: 100px;
     line-height: 1em;
     border: none;
     color: ghostwhite;
     padding: 5px;
     text-align: center;
     text-decoration: none;
     display: inline-block;
     font-size: 1rem;
     margin: 4px 2px;
 }
 button.primary {
     background-color: #F35537;
 }
 button.alternate {
     background-color: #77C4D3;
 }
 button:focus {
     outline: none;
 }
 button:hover {
     box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
 }
 button:active {
     transform: translateY(4px);
 }
 input {
     height: 20px;
     padding: 10px;
 }
 a{
     color: #77C4D3;
 }
 .flexWrapper {
     display:flex;
 }
 .flexRight {
     margin-left: auto;
 }
 .error {
     color: #F35537;
 }
 
 .myHeader{
   text-align: center;
   margin-botton: 10px;
   color: black;
   background-color: white;
 } 
 .footer {
   position: fixed;
   left: 0;
   bottom: 0;
   width: 100%;
   background-color: white;
   text-align: center;
 }
 .footer a{
   color: teal;
   text-decoration: none;
 }

</style>
