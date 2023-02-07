<template>
  <div class="app">
    <timer-app />
  </div>
</template>

<script>
import TimerApp from "./components/TimerApp.vue";
export default {
  components: { TimerApp },
  name: "App",
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  width: 900px;
  margin: 0 auto;
}
</style>
