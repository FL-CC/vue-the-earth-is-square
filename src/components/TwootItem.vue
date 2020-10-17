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

<style lang="scss" scoped>
.tw_container {
  @include container;

  text-align: left;
  min-height: 40px;
  margin-bottom: 12px;
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

.tw_content {
  font-size: $f-size4;
  color: $fc-dark3;
}

.tw_headertitle > h3 {
  margin: 0;
}

h3 {
  font-weight: bold;
  margin: 0;
  font-size: $f-size5;
  color: $fc-dark2;
}

h4 {
  margin: 0;
  font-weight: bold;
  font-size: $f-size3;
  color: $fc-dark1;
}
</style>