<template>
  <div id="app">
    <nav>
      <div class="navigation__logo">
        Twitter
      </div>
      <div class="navigation__user" style="display: flex; align-items: center; ">
        <img src="https://picsum.photos/40/40" alt="" style="border-radius: 50%; margin-right: 20px" height="40" width="40">
        @elzodxon_me
      </div>
    </nav>

    <userProfile />
  </div>
</template>

<script>
import userProfile from "@/components/userProfile";

export default {
  name: "App",
  components: { userProfile },
};
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  min-height: 100vh;
  background: #f3f5fa;
}

nav{
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 30px 5%;
  background: #2c3e50;
  color: white;
}

.navigation__logo{
  font-weight: bold;
  font-size: 24px;
}

.navigation__user{
  font-weight: normal;
  font-size: 24px;
}


</style>
