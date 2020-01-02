<template>
  <div id="app">
    <PracticeOptions />
  </div>
</template>

<script>
import PracticeOptions from "./components/PracticeOptions/PracticeOptions";

export default {
  name: "app",
  components: {
    PracticeOptions
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: black;
}
</style>
