<template>
  <div class="up_container">
    <h1 class="up_title">@{{ user.username }}</h1>
    <div class="up_badge">Admin</div>
    <div class="up_section">
      <span class="up_name">{{ user.name }}</span>
      <span class="up_followers">{{ user.follower }}</span>
      <button @click="followUser">Follow</button>
    </div>
    <div class="up_newTwoot">
      <form
        class="up_newTweetForm"
        @submit.prevent="createTwoot"
        :class="{ limit: newTwootCharCount > 180 }"
      >
        <label for="newTwoot"
          ><strong>New Twoot ({{ newTwootCharCount }} / 180 )</strong></label
        >
        <textarea id="newTwoot" rows="4" v-model="newTwootContent" />
        <label for="twootType"><strong>Type :</strong></label>
        <select id="twootType" v-model="newTwootType">
          <option v-for="type in twootTypes" :value="type.value" :key="type.id">
            {{ type.name }}
          </option>
        </select>
        <button type="submit">Twoot</button>
      </form>
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
  data() {
    return {
      newTwootType: "instant",
      newTwootContent: "",
      twootTypes: [
        { id: 1, value: "draft", name: "Draft" },
        { id: 2, value: "instant", name: "Instant Twoot" },
      ],
    };
  },
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
    newTwootCharCount() {
      return this.newTwootContent.length;
    },
  },
  methods: {
    followUser() {
      this.followers++;
    },
    createTwoot() {
      if (this.newTwootContent && this.newTwootType != "draft") {
        this.$emit("create-twoot", this.newTwootContent, this.user);
      }
      this.newTwootContent = "";
    },
  },
  mounted() {
    setTimeout(() => {
      this.followUser();
    }, 1000);
  },
};
</script>

<style lang="scss" scoped>
.up_container {
  display: flex;
  flex: 1 0 300px;
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

  .up_section {
    display: flex;
    flex-direction: row;
    justify-content: space-between;

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
  }

  .up_newTwoot {
    display: flex;
    flex-direction: column;
    padding: 20px 8px 8px 8px;

    .up_newTweetForm {
      display: flex;
      flex-direction: column;

      &.limit {
        border: 2px solid red;
        border-radius: 2px;
      }
    }
  }
}
</style>