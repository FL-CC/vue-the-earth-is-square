<template>
  <div class="app_section">
    <UserProfile :user="user" />
    <div class="app_twootContainer">
      <TwootItem v-for="twoot in user.twoots" :twoot="twoot" :key="twoot.id" />
    </div>
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile";
import TwootItem from "./components/TwootItem";

export default {
  name: "App",
  components: {
    UserProfile,
    TwootItem,
  },
  data() {
    return {
      user: {
        username: "Fili96",
        name: "Fili Catos",
        follower: 0,
        twoots: [
          {
            id: 1,
            content: "Twooter is Awesome!",
          },
          {
            id: 2,
            content: "It's growing",
          },
        ],
      },
    };
  },

  watch: {},
  computed: {},
  methods: {},
  mounted() {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 500px;
  text-align: center;
  color: #2c3e50;
  display: flex;
  padding: 20px;
  flex-direction: row;
  justify-content: flex-start;
  align-items: flex-start;
  /* justify-items: flex-end; */

  background-color: #eeeeff;
}

.app_twootContainer {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  flex: 1 1 400;
  justify-content: stretch;
  padding-left: 50px;
  padding-right: 50px;
  width: 100%;
}
.app_section {
  display: flex;
  justify-content: stretch;
  width: 100%;
}
</style>
