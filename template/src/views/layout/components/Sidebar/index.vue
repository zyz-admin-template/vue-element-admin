<template>
  <el-scrollbar style="z-index: 10000000" wrap-class="scrollbar-wrapper">
    <el-menu
      :show-timeout="200"
      :default-active="$route.path"
      :collapse="isCollapse"
      mode="vertical"
      background-color="rgb(48, 65, 86)"
      text-color="#bfcbd9"
      active-text-color="#0190fe"
    >
      <sidebar-item
        v-for="route in permission_routers"
        :key="route.path"
        :item="route"
        :base-path="route.path"
      />
    </el-menu>
  </el-scrollbar>
</template>

<script>
import { mapGetters } from "vuex";
import SidebarItem from "./SidebarItem";

export default {
  components: { SidebarItem },
  computed: {
    ...mapGetters(["permission_routers", "sidebar"]),
    isCollapse() {
      return !this.sidebar.opened;
    }
  }
};
</script>

<style lang="scss">
.el-menu-item {
  &:hover {
    background-color: rgb(27, 40, 56) !important;
  }
}
</style>
