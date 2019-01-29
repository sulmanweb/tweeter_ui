<template>
  <div>
    <div class="pull-right">
      <log-out></log-out>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-md-8 col-md-offset-2">
          <h1>Welcome To Tweeter</h1>
          <create-tweet></create-tweet>
          <hr>
          <list-tweets></list-tweets>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CreateTweet from "@/components/CreateTweet.vue";
import ListTweets from "@/components/ListTweets.vue";
import LogOut from "@/components/LogOut.vue";
export default {
  name: "home",
  components: {
    CreateTweet,
    ListTweets,
    LogOut
  },
  methods: {
    getUser() {
      var token = localStorage.getItem("token");
      if (token === undefined || token === null) {
        this.$router.push({ name: "sign_in" });
      }
    }
  },
  mounted() {
    this.getUser();
  }
};
</script>
