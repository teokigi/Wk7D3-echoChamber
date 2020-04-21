<template lang="html">
  <body id="app">
      <noscript>
        <strong>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work properly without JavaScript enabled. Please enable it to continue.</strong>
      </noscript>
      <h1> The Echo Chamber </h1>
      <div>
          Total dislikes: {{totalLikes}},
          <label for="numberInput">View dislikes greater than: </label>
          <input type="number" name="numberInput" v-model="likeFilter" @change="filteredTweets" id="numberInput" min="0">

      </div>
      <div id="tweetBody">
        <echo-chamber-user v-for="(tweet,index) in filteredTweets" :key="index" :tweet="tweet" v-on:addMessage="theMessage =>{addMessage(theMessage)}"></echo-chamber-user>
      </div>

      <div>

      </div>

  </div>
</body>
</template>

<script>

  import EchoChamberUser from './components/EchoChamberUser.vue';

  export default {
    name:'app',
    data() {
      return {
        likeFilter:0,
        tweets:[
          {
            id: 1,
            name: 'James',
            handle: '@jokerjames',
            img: 'https://semantic-ui.com/images/avatar2/large/matthew.png',
            tweet: "If you don't succeed, dust yourself off and try again.",
            likes: 10,
          },
          {
            id: 2,
            name: 'Fatima',
            handle: '@fantasticfatima',
            img: 'https://semantic-ui.com/images/avatar2/large/molly.png',
            tweet: 'Better late than never but never late is better.',
            likes: 12,
          },
          {
            id: 3,
            name: 'Xin',
            handle: '@xeroxin',
            img: 'https://semantic-ui.com/images/avatar2/large/elyse.png',
            tweet: 'Beauty in the struggle, ugliness in the success.',
            likes: 18,
          }
        ]
        }
      },
      components:{
        'echo-chamber-user' : EchoChamberUser
      },
      computed:{
        totalLikes: function(){
          return this.tweets.reduce((total,tweet)=> total + tweet.likes,0);
        },
        filteredTweets(){
          return this.tweets.filter(tweet => tweet.likes>=this.likeFilter)
        }
      },
      methods:{
        addMessage(message){
          this.tweets.unshift(message);
        }
      }
}
// MVP
// done - Display a list of tweets with all the details.
// done - Display the user avatar along with the tweet
// Use computed property to display the total number of likes for all tweets.
// Extensions
// done - Allow user to add a new tweet. Use an existing avatar links. (Add the Form to the App component)
// done - Filter the tweets to only display ones with over 10 likes
// Change the styling for tweets with over 10 likes
</script>

<style lang="css" scoped>
#app{
  width:100%;
  height:100%;
  margin:0px;
  padding:0px;
  background-color:lightblue;
  text-align:center;
  display:flex;
  flex-direction:column;
  align-items:center;
}
div{
  margin:5px;
}
#tweetBody{
  background-color:yellow;
  border-radius:25px;

}
#numberInput{
  border-style:none;
  width:30px;
  text-align:center;
  background-color:inherit;
}
</style>
