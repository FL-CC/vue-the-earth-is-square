<template>
  <div class="sbi_container">{{ item.title }}</div>
</template>

<script>
export default {
  name: "SideBarItem",
  props: {
    item: {
      required: true,
      type: Object,
    },
  },
};
</script>

<style>
.sbi_container {
  transition: all 1 ease;
  white-space: nowrap;
  padding: 4px 8px;
  border-radius: 3px;
  box-shadow: 10px 11px 14px -9px rgba(0, 0, 0, 0.32);
  background: white;
}

.sbi_container:hover {
  transform: scale(1.1);
  font-weight: bold;
  cursor: pointer;
}
</style>