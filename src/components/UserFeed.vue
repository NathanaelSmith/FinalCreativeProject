<template>
  <div class="feed">
    <div>
      <form enctype="multipart/form-data" v-on:submit.prevent="tweet" class="tweetForm">
        <textarea v-model="text"  placeholder="My Note..." rows="5" /><br/>
	<div class="buttonWrap">
	  <button class="noteBut" type="submit">Make Note</button>
	</div>
      </form>
    </div>
    <feed-list v-bind:feed="feed" />
  </div>
</template>

<script>
 import FeedList from './FeedList';
 export default {
   name: 'UserFeed',
   components: { FeedList },
   data () {
     return {
       text: '',
     }
   },
   computed: {
      feed: function() {
      return this.$store.getters.feed;
     },
   },
   created: function() {
     this.$store.dispatch('getFeed');
   },
   methods: {
     tweet: function() {
       this.$store.dispatch('addTweet',{
         tweet: this.text,
         
       }).then(tweet => {
	 this.text = "";
         
       });
     },
   }
 }
</script>

<style scoped>
 .feed {
     margin-left: 4%;
     width: 90%;
 }
 .noteBut{
   color: white;
   background-color: teal;
   padding: 7px;
   width: 100%;
   text-align: center;
 }

 .tweetForm {
     background: #eee;
     padding: 10px;
     margin-bottom: 10px;
 }
 .buttonWrap {
     width: 100%;
     display: flex;
 }
 button {
     margin-left: auto;
     height: 2em;
     font-size: 0.9em;
 }
 textarea {
     width: 100%;
     height: 5em;
     padding: 2px;
     margin-bottom: 5px;
     resize: none;
     box-sizing: border-box;
     font-size: 16px;
 }
</style>
