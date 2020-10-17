<template>
  <div class="sb_container">
    <div class="sb_content">
      <SideBarItem
        class="sb_item"
        v-for="sideBarItem in sideBarItems"
        :item="sideBarItem"
        :key="sideBarItem.id"
      />
    </div>
  </div>
</template>

<script>
import SideBarItem from "./SideBarItem";

export default {
  name: "",
  components: {
    SideBarItem,
  },
  data() {
    return {
      sideBarItems: [
        {
          id: 1,
          title: "Item 1",
        },
        {
          id: 2,
          title: "Item 2",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.sb_container {
  padding: 16px 20px;

  .sb_content {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;

    .sb_item {
      margin-bottom: 8px;
    }
  }
}
</style>