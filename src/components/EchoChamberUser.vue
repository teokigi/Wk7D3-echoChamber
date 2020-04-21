<template lang="html">
  <div id="echo-chamber-user">
      <div class="image">
        <img v-bind:src="tweet.img">
      </div>
      <div class="text">
      <div class="tweetText">
        <div class="tweeter"> {{tweet.name}} tweeted:</div>
        <div class="tweeterName"> {{tweet.name}}</div>
        <div class="tweeterHandle"> {{tweet.handle}}</div>
        <div class="tweeterMessage"> {{tweet.tweet}}</div>
        <div class="tweeterResponses">dislikes: {{tweet.likes}}</div>
      </div>
      <div class="form">
        <form v-on:submit.prevent="newMessage()" >
          <input type="text" v-model="newTweetMessage.tweet" class="textInput">
          <input type="submit" value="say more">
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
  background-color:skyblue;
  padding:5px;
}
.tweeter{

}
.image{
  width:100px;
}
img{
  height:100px;
  width:^100px;
  border-radius:50px;
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
  text-align:center;
}
</style>
