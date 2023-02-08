<template>
  <div id="app">
    <header></header>
    <router-view />
  </div>
</template>
<script lang="ts">
import { defineComponent } from "@vue/composition-api";

export default defineComponent({
  setup() {
    if (!window.localStorage.getItem("todoList")) {
      window.localStorage.setItem("todoList", JSON.stringify([]));
    }
  },
});
</script>

<style lang="postcss" scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

header {
  @apply h-14 w-full bg-gray-700;
}
</style>
