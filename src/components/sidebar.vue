<template>
  <div class="sidebar">
    <div @click="onMenuClick">
    <MenuIcon />
    </div>
    <div class="sidebar__item" v-for="item in sidebar" :key="item.name">
      <component :is="item.component"></component>
      <!-- <p v-if="!full" class="itemname">{{item.name}}</p> -->
    </div>
  </div>
</template>

<script>
import MenuIcon from "./icons/menuIcon";
import HomeIcon from "./icons/homeIcon";
import LotteryIcon from "./icons/lotteryIcon";

export default {
  name: "Sidebar",
  components: {
    MenuIcon,
    HomeIcon,
    LotteryIcon,
  },
  props: {
    full: {
      type: Boolean,
      default: true,
    },
    onMenuClick: {
      type: Function
    }
  },
  data() {
    return {
      sidebar: [
        { id: 0, component: "HomeIcon", name: "Home" },
        { id: 1, component: "LotteryIcon", name: "Lottery" },
      ],
    };
  },
};
</script>

<style scoped lang="scss">
@import "../theme/scss/variables.scss";
.sidebar {
  background-color: $darkBlue2;
  padding: 3.093rem 1.306rem;
  border-top-right-radius: 2.687rem;
  border-bottom-right-radius: 2.687rem;
  &__item {
    display: flex;
    align-items: center;
    color: $white;
    margin-bottom: 3.937rem;
    & img {
      margin-right: 1rem;
    }
  }
  .itemname{
    margin-left: 1rem;
  }
}
</style>