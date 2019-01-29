<template>
  <div>
    <form action="#" @submit.prevent="submitform">
      <div class="form-group">
        <label for="body">Tweet</label>
        <input
          type="text"
          class="form-control"
          id="body"
          placeholder="Enter New Tweet"
          v-model="formData.body"
        >
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "CreateTweet",
  data() {
    return {
      formData: {}
    };
  },
  methods: {
    submitform() {
      var headers = {
        headers: {
          token: localStorage.getItem("token")
        }
      };
      this.$http
        .post("http://localhost:3000/tweets", this.formData, headers)
        .then(() => {
          this.formData = {};
        })
        .catch(() => {});
    }
  }
};
</script>
