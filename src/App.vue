<template>
<div id="app">
  @{{user.username}} - {{fullName}}
  <strong>Followers:  {{followers}}</strong>
</div>
<button @click="followUser">
  Follow
</button>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user : {
        id:1,
        username: "Twilli",
        firstName: "Fili",
        lastName: "Catos",
        email: "fl@catos.de",
        isAdmin: true
      }
    }
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} gained a follower.`, {oldFollowerCount, newFollowerCount});
      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.lastName}, ${this.user.firstName}`;
    }
  },
  methods: {
    followUser() {
      this.followers++;
    }
  },
  mounted() {
    setTimeout(() => {
    this.followUser();}, 1000);
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
}
</style>
