<template>
  <div class="user-profile">
    <div class="user-profile__user-panel">
      <img
        src="https://picsum.photos/250/250"
        alt=""
        class="user-profile__userpic"
        height="250"
        width="250"
      />
      <div class="user-profile__admin-badge" v-if="user.isAdmin">Admin</div>
      <div class="user-profile__admin-badge" v-else-if="user.isModerator">
        Moderator
      </div>
      <img
        class="user-profile__verified-badge"
        src="../badge.png"
        alt=""
        v-if="user.isVerified"
        height="30px"
        width="30px"
      />
      <h1 class="user-profile__firstname">
        {{ this.user.firstName }} {{ this.user.secondName }}
      </h1>
      <a class="user-profile__username" href="">@{{ this.user.username }}</a>
      <div class="user-profile__follower-count">
        <strong>Followers:</strong>{{ this.followers }}
        <strong>Following:</strong>{{ this.following }}
      </div>

      <form
        action=""
        class="user-profile__create-tweet"
        @submit.prevent="createNewTweet"
        :class="{'exceeded': newTweetCharactersCount> 180}"
      >
        <label for="newTweet"><strong>New Tweet</strong> ({{newTweetCharactersCount}}/180)</label>
        <textarea
          name="newTweet"
          id="user-profile__tweet-area"
          cols="50"
          rows="4"
          v-model="newTweetContent"
        ></textarea>

        <div class="user-profile__create-tweet-type">
          <label for="tweetType">Tweet type</label>
          <select name="tweetTyoe" id="newTweetType" v-model="selectedTweet">
            <option
              :value="option.value"
              v-for="(option, index) in tweetTypes"
              :key="index"
            >
              {{ option.name }}
            </option>
          </select>

          <button>Tweet</button>
        </div>
      </form>
    </div>

    <div class="user-profile__tweets-wrapper">
      <tweetItem
        v-for="tweet in user.tweets"
        :key="tweet.id"
        :username="user.username"
        :tweet="tweet"
        @fav="toggleFav"
      />
    </div>
  </div>
</template>

<script>
import tweetItem from "@/components/tweetitem";
export default {
  name: "App",
  components: { tweetItem },
  data() {
    return {
      newTweetContent: "",
      selectedTweet: "instant",
      tweetTypes: [
        {
          value: "draft",
          name: "Draft",
        },
        {
          value: "instant",
          name: "Instant",
        },
      ],
      followers: 0,
      following: 0,
      user: {
        id: 1,
        username: "elzodxon_me",
        firstName: "Elzodxon",
        secondName: "Sharofaddinov",
        email: "elzodxon@gmail.com",
        isAdmin: true,
        isModerator: false,
        isVerified: false,
        tweets: [
          {
            id: 1,
            content: "My tweeter clone is amazing!",
          },
          {
            id: 2,
            content: "Don't forget to follow me",
          },
          {
            id: 3,
            content: "Don't forget to follow me",
          },
          {
            id: 4,
            content: "Don't forget to follow me",
          },
          {
            id: 5,
            content: "Don't forget to follow me",
          },
          {
            id: 6,
            content: "Don't forget to follow me",
          },
          {
            id: 7,
            content: "Don't forget to follow me",
          },
          {
            id: 8,
            content: "Don't forget to follow me",
          },
        ],
      },
    };
  },
  watch: {
    followers(newFollower, oldFollower) {
      if (oldFollower < newFollower) {
        console.log(`${this.user.username} has gained follower`);
      }
    },
  },
  computed: {
   newTweetCharactersCount(){
     return this.newTweetContent.length
   }
  },

  methods: {
    followUser() {
      return this.followers++;
    },
    toggleFav(id) {
      console.log(`Favorite tweet is ${id}`);
    },
    createNewTweet() {
      if (this.newTweetContent && this.selectedTweet !== "draft") {
        this.user.tweets.unshift({
          id: this.user.tweets.length + 1,
          content: this.newTweetContent,
        });

        this.newTweetContent = "";
      }
    },
  },
  mounted() {
    this.followUser();
  },
};
</script>

<style scoped>
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  width: 100%;
  padding-top: 5%;
}
.user-profile__user-panel {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-right: 50px;
  margin-left: 50px;
  padding: 20px;
  border: #dfe3e8 2px solid;
  border-radius: 20px;
  height: 80%;
}

.user-profile__userpic {
  border-radius: 50%;
}

.user-profile__username {
  font-size: 25px;
  font-weight: 400;
  padding-bottom: 20px;
  text-decoration: none;
  color: #2c3e50;
}

.user-profile__username:hover {
  text-decoration: underline;
}

.user-profile__admin-badge {
  background: black;
  color: white;
  font-size: 10px;
  padding: 5px;
  text-align: center;
  border-radius: 5px;
  font-weight: bold;
  margin-top: 10px;
}

.user-profile__verified-badge {
  margin-top: 10px;
}

.user-profile__create-tweet {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}

.user-profile__tweets-wrapper{
  display: grid;
  gap: 10px;
}

.exceeded{
  color: red;
  border-color: red;
}

</style>
