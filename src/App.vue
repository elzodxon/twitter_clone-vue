<template>
  <div id="app">



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
  padding: 10px 5%;
  background: #2c3e50;
  color: white;
}

.navigation__logo,
.navigation__user{
  font-weight: bold;
  font-size: 24px;
}


</style>
