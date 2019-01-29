<template>
  <div>
    <pre v-for="tweet in tweets" :key="tweet.id">
      {{tweet.body}}
      <hr>
      {{tweet.user.name}}
    </pre>
  </div>
</template>
<script>
export default {
  name: "ListTweets",
  data() {
    return {
      tweets: []
    };
  },
  methods: {
    getAllTweets() {
      this.$http
        .get("http://localhost:3000/tweets")
        .then(res => {
          this.tweets = res.data;
        })
        .catch(() => {});
    }
  },
  mounted() {
    this.getAllTweets();
  }
};
</script>
