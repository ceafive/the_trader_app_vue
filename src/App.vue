<template>
  <div>
    <Header></Header>
    <div class="mx-64">
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
export default {
  components: {
    Header
  },
  created() {
    this.$store.dispatch("initStocks");
  }
};
</script>

<style lang="">
body {
  font-family: "Raleway", sans-serif;
}
</style>
