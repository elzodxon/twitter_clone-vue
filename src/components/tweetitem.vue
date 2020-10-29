<template>
  <div class="tweetItem" @click="favouriteTweet(tweet.id)">
    <div class="user-profile__tweet">
      <div class="tweet-item__user">@{{ username }}</div>
      <div class="tweet-item__content">
        {{ tweet.content }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "tweetItem",
  props: {
    username: {
      type: String,
      required: true,
    },
    tweet: {
      type: Object,
      required: true,
    },
  },
  methods: {
    favouriteTweet(id) {
      this.$emit("fav", id);
    },
  },
};
</script>

<style scoped>
.tweetItem {
  padding: 20px;
  background: white;
  border-radius: 5px;
  border: 1px solid #2c3e50;
  box-sizing: border-box;
  cursor: pointer;
  transition: all 0.25s ease;
  margin-bottom: 20px;
}

.user-profile__tweet {
}

.tweetItem:hover {
  transform: scale(1.05, 1.05);
}

.tweet-item__user {
  color: #2c3e50;
  font-weight: bold;
  font-size: 25px;
}
</style>
