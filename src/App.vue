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
</style>
