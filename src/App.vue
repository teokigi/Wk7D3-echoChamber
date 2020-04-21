<template lang="html">
  <div>
    <echo-chamber-user v-for="(tweet,index) in tweets" :key="index" :tweet="tweet"></echo-chamber-user>
  </div>
</template>

<script>

  import EchoChamberUser from './components/EchoChamberUser.vue';

  export default {
    name:'app',
    data() {
      return {
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
      }
}
// MVP
// Display a list of tweets with all the details.
// Display the user avatar along with the tweet
// Use computed property to display the total number of likes for all tweets.
// Extensions
// Allow user to add a new tweet. Use an existing avatar links. (Add the Form to the App component)
// Filter the tweets to only display ones with over 10 likes
// Change the styling for tweets with over 10 likes
</script>

<style lang="css" scoped>
body{
  width:100%;
  height:100%;
  background-color:blue;
  border-style:1;
}
</style>
