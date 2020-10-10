<template>
<div id="app">
  <UserProfile />
</div>
 
</template>

<script>
import UserProfile from "./components/UserProfile";

export default {
  name: 'App',
  data() {},
  components: {
    UserProfile
  },
  watch: {
  },
  computed: {
    
  },
  methods: {
    
  },
  mounted() {}
   
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  background-color: #eeeeff;
}
</style>
