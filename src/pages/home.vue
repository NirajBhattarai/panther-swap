<template>
  <div>
    <div class="content__wrapper">
      <div :class="sidebarClass">
        <Sidebar :full="fullSidebar" :onMenuClick="handleSidebar" />
      </div>
      <div :class="mainContentClass">
        <Header :onMenuClick="handleSidebar" />
        <Lottery />
        <div class="cards_wrapper">
          <ToggleButton :onToggle="handleToggler" :active="activeSection" />
          <NextDraw v-if="activeSection===1" />
          <PostDraw v-if="activeSection===2" />
          <AdminDraw v-if="activeSection===3" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "../components/header.vue";
import Sidebar from "../components/sidebar.vue";
import Lottery from "../components/lottery.vue";
import ToggleButton from "../components/buttons/toggleButton.vue";
import NextDraw from "../components/nextDraw.vue";
import PostDraw from "../components/postDraw.vue";
import AdminDraw from "../components/adminDraw.vue";

export default {
  name: "Home",
  components: {
    Header,
    Lottery,
    ToggleButton,
    Sidebar,
    NextDraw,
    PostDraw,
    AdminDraw,
  },
  data() {
    return {
      fullSidebar: true,
      sidebarClass: "half__sidebar",
      mainContentClass: "half__content",
      activeSection: "Next draw",
    };
  },
  methods: {
    handleSidebar() {
      console.log("hello");
      this.fullSidebar = !this.fullSidebar;
      if (this.sidebarClass === "full_sidebar") {
        this.sidebarClass = "half__sidebar";
      } else {
        this.sidebarClass = "full_sidebar";
      }

      if (this.mainContentClass === "full_content") {
        this.mainContentClass = "half__content";
      } else {
        this.mainContentClass = "full_content";
      }
    },
    handleToggler(buttonName) {
      this.activeSection = buttonName;
    },
  },
};
</script>

<style scoped lang="scss">
@import "../theme/scss/variables.scss";
.cards_wrapper {
  background-color: $blue;
  padding: 2rem;
}
.content__wrapper {
  display: flex;
  height: calc(100vh);
  overflow-y: hidden;
  background-color: $darkBlue;
}

.full_sidebar {
  width: 15rem;
  align-self: stretch;
  background-color: $darkBlue2;
  transition: all 0.4s;
}
.half__sidebar {
  width: 5rem;
  align-self: stretch;
  background-color: $darkBlue2;
  transition: all 0.4s;
  border-top-right-radius: 2.687rem;
  border-bottom-right-radius: 2.687rem;
}
.full_content {
  width: calc(100% - 15rem);
  transition: all 0.4s;
  overflow-y: auto;
}
.half__content {
  width: calc(100% - 5rem);
  transition: all 0.4s;
  overflow-y: auto;
}
</style>