<template lang="html">
  <div v-bind:id="tweet.likes <= 10 ? 'echo-chamber-user': 'echo-chamber-user-disliked'">
      <div class="image">
        <img v-bind:src="tweet.img" id="image">
      </div>
      <div class="text">
      <div class="tweetText">
        <div class="tweeter"> {{tweet.name}} tweeted:</div>
        <div class="tweeterName"> {{tweet.name}}</div>
        <div class="tweeterHandle"> {{tweet.handle}}</div>
        <div class="tweeterMessage"> {{tweet.tweet}}</div>
        <div class="tweeterResponses"><img class="icon" v-on:click="tweet.likes++"src="https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/120/samsung/220/thumbs-down-sign_1f44e.png"> {{tweet.likes}}</div>
      </div>
      <div class="form">
        <form v-on:submit.prevent="newMessage()" >
          <input type="text" v-model="newTweetMessage.tweet" class="textInput" placeholder="Enter new message here">
          <input type="submit" v-bind:value="`Make ${tweet.name} post`" class="submit">
        </form>
      </div>
    </div>

  </div>
</template>
 <script>
export default {
  name: 'echo-chamber-user',
  props: ['tweet'],
  data(){
    return{
    newTweetMessage: {  id:this.tweet.id,
                        name:this.tweet.name,
                        handle: this.tweet.handle,
                        tweet:"",
                        img: this.tweet.img,
                        tweet: this.newTweetMessage,
                        likes: 0,
                      }
  }
},
methods:{
  newMessage(){
    this.$emit('addMessage',this.newTweetMessage)
    this.newTweetMessage=""
  }
}
}
</script>

<style lang="css" scoped>
#echo-chamber-user{
  width:640px;
  display:flex;
  flex-direction:row;
  border-radius:20px;
  background-color:lightgreen;
  padding:5px;
  margin:15px;
  box-shadow: 0px 0px 20px black;
}
#echo-chamber-user-disliked{
  width:640px;
  display:flex;
  flex-direction:row;
  border-radius:20px;
  background-color:#FF7777;
  padding:5px;
  color:darkred;
  margin:15px;
  box-shadow: 0px 0px 20px black;
}
.tweeter{

}
.image{
  width:100px;
}
#image{
  height:90px;
  width:90px;
  border-radius:50px;
  box-shadow: 0px 0px 15px white;
}
.icon{
  height: 25px;
  width: 25px;
}
.tweetText{
  text-align:left;
  border-style:dotted;
  width:525px;
  padding:5px;
  border-radius:15px;
}
.tweeter{
  color:grey;
  font-family:georgia;
  font-size:10px
}
.tweeterName{
  font-family:impact;
}
.tweeterHandle{
  font-family:'comic sans ms';

  font-size: 10px;
  color:#555555;
}
.tweeterMessage{
  font-family:monospace;
  font-size:25px;
}
.tweeterResponses{
  text-align:right;
  font-size:30px;
}
.textInput{
  margin:2px;
  padding:2px;
  width:300px;
  border-style:none;
  border-radius:5px;
  box-shadow: inset 0px 0px 4px blue;
}
.submit{
  border-radius:10px;
  color:white;
  width:150px;
  background-color:#9999FF;
}
</style>
