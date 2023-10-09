<template>
  <div id="app">
    <ColumnOne />
    <ColumnTwo />
    <ColumnThree />
    <ColumnFour />
  </div>
</template>

<script>
import ColumnOne from "./components/ColumnOne.vue";
import ColumnTwo from "./components/ColumnTwo.vue";
import ColumnThree from "./components/ColumnThree.vue";
import ColumnFour from "./components/ColumnFour.vue";

export default {
  name: "App",
  components: {
    ColumnOne,
    ColumnTwo,
    ColumnThree,
    ColumnFour,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 16px;
  margin-top: 50px;
}
</style>
