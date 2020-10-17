<template>
  <div class="up_outer">
    <div class="up_container">
      <h1 class="up_title">@{{ user.username }}</h1>
      <div class="up_badge">Admin</div>
      <div class="up_section">
        <span class="up_name">{{ user.name }}</span>
      </div>
    </div>
    <div class="up_newTwoot container">
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
        <button
          class="btn"
          :class="{ danger: newTwootCharCount > 180 }"
          type="submit"
        >
          Twoot
        </button>
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
    createTwoot() {
      if (this.newTwootContent && this.newTwootType != "draft") {
        this.$emit("create-twoot", this.newTwootContent, this.user);
      }
      this.newTwootContent = "";
    },
  },
  mounted() {
    // setTimeout(() => {
    //   this.followUser();
    // }, 1000);
  },
};
</script>

<style lang="scss" scoped>
.up_outer {
  display: flex;
  flex-direction: column;
  flex: 1 0 300px;
}

.up_container {
  @include container;

  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  text-align: left;
  justify-self: self-start;

  .up_title {
    font-size: $f-size3;
    margin-bottom: $m-2;
    margin-top: $m-1;
  }

  .up_badge {
    font-size: $f-size5;
    font-weight: bolder;
    padding: $p-1;
    border-radius: $br-1;

    background-color: $primary;
    color: $white;
    margin-right: auto;
    margin-top: 0;
    margin-bottom: $m-3;
  }

  .up_section {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
}
.up_newTwoot {
  display: flex;
  flex-direction: column;
  margin-top: $m-3;
  font-family: $default-font-family;
  color: $fc-dark1;

  .up_newTweetForm {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: space-between;

    textarea#newTwoot {
      margin-top: $m-2 !important;
      border: 2px solid $accent;
      padding: $p-2;
      align-self: stretch;
    }

    label {
      margin-top: $m-3;
    }

    select {
      @include button;
      margin: $m-2 0;
      padding: $p-1;

      option {
        background-color: $primary;
      }
    }

    button {
      align-self: stretch;
    }
  }
}
</style>