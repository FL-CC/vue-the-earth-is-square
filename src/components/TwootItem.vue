<template>
  <div class="tw_container" @click="favouriteItem(twoot.id)">
    <div class="tw_headerrow">
      <div class="tw_headertitle">
        <h4>{{ twoot.title }}</h4>
      </div>
      <div class="tw_username">
        <h3>@{{ twoot?.user.username }}</h3>
      </div>
    </div>
    <div class="tw_content">{{ twoot?.content }}</div>
  </div>
</template>

<script>
export default {
  name: "TwootItem",
  props: {
    user: {
      required: true,
      type: Object,
    },
    twoot: {
      required: true,
      type: Object,
    },
  },
  methods: {
    favouriteItem(id) {
      this.$emit("favourite", id);
    },
  },
};
</script>

<style>
.tw_container {
  text-align: left;
  min-height: 40px;
  padding: 8px;
  background-color: white;
  border-radius: 5px;
  margin-bottom: 12px;
  box-shadow: 10px 11px 14px -9px rgba(0, 0, 0, 0.32);
  transition-duration: 0.15s;
  transition-timing-function: ease;
  transition-property: all;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.tw_container:hover {
  transform: scale(1.02, 1.02);
}

.tw_headerrow {
  display: flex;
  justify-content: space-between;
}

.tw_headertitle > h3 {
  margin: 0;
}

.tw_container {
  color: #847985;
}

h3 {
  font-weight: bold;
  margin: 0;
  font-size: 15px;
  color: #626758;
}

h4 {
  margin: 0;
  font-weight: bold;
  font-size: 13px;
  color: #626758;
}
</style>