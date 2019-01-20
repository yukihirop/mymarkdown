<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import Editor from "./components/Editor.vue";

export default {
  name: "app"
};
</script>