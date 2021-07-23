<template>
  <router-view />
</template>

<script>
import "@fortawesome/fontawesome-free/css/all.css";
import "@fortawesome/fontawesome-free/js/all.js";
import "./theme/scss/variables.scss";
import "./theme/scss/common.scss"

export default {
  name: "App"
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Mitr:wght@200;300;400;500;600;700&display=swap");

* {
  padding: 0;
  margin: 0;
}
</style>
