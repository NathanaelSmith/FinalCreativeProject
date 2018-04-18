<template>
  <div>
    <div v-for="item in feed" class="item">
      <p class="idline">Note from {{item.created | since}}'s ago.  <span class="closebtn" onclick="this.parentElement.parentElement.style.display='none';">&times;</span> </p>
      <p>{{item.tweet}}</p>
    </div>
  </div>
</template>

<script>
 import moment from 'moment';
 export default {
   name: 'FeedList',
   props: ['feed'],
   filters: {
     since: function(datetime) {
       moment.locale('en', {
	 relativeTime: {
	   future: 'in %s',
	   past: '%s',
	   s:  'seconds',
	   ss: '%ss',
	   m:  '1m',
	   mm: '%dm',
	   h:  'h',
	   hh: '%dh',
	   d:  'd',
	   dd: '%dd',
	   M:  ' month',
	   MM: '%dM',
	   y:  'a year',
	   yy: '%dY'
	 }
       });
       return moment(datetime).fromNow();
     },
   },
   
 }
</script>

<style scoped>
 .item {
     background-color:white;
     color: black;
     padding: 10px;
     margin-bottom: 5px;
 }
 .tweet {
     margin-top: 0px;
 }
 .idline {
     margin-bottom: 0px;
 }
 .user {
     font-weight: bold;
     margin-right: 10px;
 }
 .handle {
     margin-right: 10px;
     color: #666;
 }
 .time {
     float: right;
     color: #666;
 }
 .notBut{
   color: white;
   background-color: teal;
   border: none;
   padding: 5px;
   margin: 0px;
   margin-top:2px;
   margin-left: 2px;
   width: 100%;
 }
 .closebtn {
    margin-left: 15px;
    color: black;
    font-weight: bold;
    float: right;
    font-size: 22px;
    line-height: 20px;
    cursor: pointer;
    transition: 0.3s;
}
</style>
