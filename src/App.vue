<template>
  <link
    rel="stylesheet"
    href="https://fonts.googleapis.com/css?family=Volkhov"
  />

  <div class="app_layout">
    <div class="app_header">
      <div class="app_logo"></div>
      <div class="app_title">Twooter</div>
      <div class="app_userinfo"></div>
    </div>
    <div class="app_sidebar">
      <SideBar />
    </div>
    <div class="app_content">
      <router-view />

      <div class="app_section">
        <UserProfile :user="user" @create-twoot="createTwoot" />
        <div class="app_twootContainer">
          <TwootItem
            v-for="twoot in twoots"
            :twoot="twoot"
            :key="twoot.id"
            @favourite="toggleFavourite"
          />
        </div>
      </div>
    </div>
    <div class="app_footer"></div>
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile";
import TwootItem from "./components/TwootItem";
import SideBar from "./components/SideBar";

export default {
  name: "App",
  components: {
    UserProfile,
    TwootItem,
    SideBar,
  },
  data() {
    return {
      user: {
        username: "Fili96",
        name: "Fili Catos",
        follower: 0,
      },
      twoots: [
        {
          id: 1,
          title: "First twoot ever",
          content: "Twooter is Awesome!",
          user: { username: "_fili96_" },
        },
        {
          id: 2,
          title: "It's never tooo late",
          content: "It's growing",
          user: { username: "cornHolIO" },
        },
        {
          id: 3,
          title: "It's never tooo late",
          content: "It's growing",
          user: { username: "cornHolIO" },
        },
      ],
    };
  },

  watch: {},
  computed: {},
  methods: {
    toggleFavourite(id) {
      console.log(`Toggled Twoot #${id}`);
    },
    createTwoot(content, user) {
      this.twoots.unshift({
        title: "New Twoot!",
        content: content,
        id: this.twoots.length + 1,
        user: user,
      });
    },
  },
  mounted() {},
};
</script>

<style lang="scss">
@import "@/styles/global.scss";
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  height: 100%;

  .app_layout {
    display: grid;
    grid-template-columns: 1fr 7fr;
    grid-template-rows: 100px 10fr 20px;
    height: 100%;
    justify-items: stretch;
    justify-self: stretch;
    align-self: stretch;
    background-color: $accent;

    .app_content {
      padding: $p-2;
      grid-column: 2;
      grid-row: 2 / 3;
      align-self: stretch;
      justify-self: stretch;

      .app_section {
        display: flex;
        justify-content: stretch;
        width: 100%;

        .app_twootContainer {
          display: flex;
          flex-direction: column;
          align-items: stretch;
          flex: 1 1 400;
          justify-content: stretch;
          padding-left: $p-3;
          padding-right: $p-3;
          width: 100%;
        }
      }
    }
    .app_header {
      @include colors-primary;

      grid-column: 1 / span 2;
      grid-row: 1 / 2;
      display: flex;
      justify-content: space-evenly;
      align-items: center;

      .app_title {
        font-size: $f-size1;
        font-family: $comic-font-family;
      }
    }
    .app_footer {
      grid-column: 1 / span 2;
      grid-row: 3 / 4;
    }

    .app_sidebar {
      grid-column: 1 / span 1;
      grid-row: 2 / 3;
    }
  }
}
</style>
