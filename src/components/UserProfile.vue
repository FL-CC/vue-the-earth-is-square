<template>
  <div class="up_container">
    <h1 class="up_title">@{{ user.username }}</h1>
    <div class="up_badge">Admin</div>
    <div class="up_section">
      <span class="up_name">{{ user.name }}</span>
      <span class="up_followers">{{ user.follower }}</span>
      <button @click="followUser">Follow</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserProfile",
  props: {
    user: {
      required: true,
      type: Object,
    },
  },
  // data() {
  //   return {
  //     followers: 0,
  //     user: {
  //       id: 1,
  //       username: "Twilli",
  //       firstName: "Fili",
  //       lastName: "Catos",
  //       email: "fl@catos.de",
  //       isAdmin: true,
  //     },
  //   };
  // },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} gained a follower.`, {
          oldFollowerCount,
          newFollowerCount,
        });
      }
    },
  },
  computed: {
    fullName() {
      return `${this.user.lastName}, ${this.user.firstName}`;
    },
  },
  methods: {
    followUser() {
      this.followers++;
    },
  },
  mounted() {
    setTimeout(() => {
      this.followUser();
    }, 1000);
  },
};
</script>

<style>
.up_container {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  text-align: left;
  width: 300px;
  border-radius: 3px;
  box-shadow: 10px 11px 14px -9px rgba(0, 0, 0, 0.32);
  background-color: white;
  padding: 8px;
  justify-self: self-start;
  align-self: flex-start;
}

.up_section {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.up_title {
  font-size: 16px;
  margin-bottom: 8px;
  margin-top: 4px;
}

.up_badge {
  font-size: 10px;
  font-weight: bolder;
  padding: 4px;
  border-radius: 5px;

  background-color: purple;
  color: white;
  margin-right: auto;
  margin-top: 0;
  margin-bottom: 16px;
}

.up_followers {
  border-radius: 20px;
  border-width: 3px;
  border-color: #454545;
  border-style: solid;
  background-color: darkcyan;
  color: white;
  width: 22px;
  display: flex;
  justify-content: space-around;
  align-content: space-around;
  padding-top: 2px;
  font-weight: bold;
}
</style>