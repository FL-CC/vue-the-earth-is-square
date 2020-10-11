<template>
  <div class="tw_container">@{{ twoot?.content }}</div>
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
};
</script>

<style>
.tw_container {
  text-align: left;
  height: 40px;
  padding: 8px;
  background-color: white;
  border-radius: 5px;
  margin-bottom: 12px;
  box-shadow: 10px 11px 14px -9px rgba(0, 0, 0, 0.32);
  transition-duration: 0.15s;
  transition-timing-function: ease;
  transition-property: all;
}

.tw_container:hover {
  transform: scale(1.02, 1.02);
}
</style>