<template>
  <div id="top">
    <Home v-if="!isLogin"></Home>
    <Editor v-if="isLogin" :user="userData"></Editor>
    <router-link :to="{name: 'terms' }">利用規約</router-link>
  </div>
</template>

<script>
import Home from "../components/Home.vue";
import Editor from "../components/Editor.vue";

export default {
  name: "app",
  data(){
    return {
      isLogin: false,
      userData: null
    }
  },
  components:{
    Home: Home,
    Editor: Editor
  },
  created: function() {
    firebase.auth().onAuthStateChanged(user => {
      console.log(user)
      if (user) {
        this.isLogin = true
        this.userData = user
      } else {
        this.isLogin = false
        this.userData = null
      }
    })
  }
}
</script>

<!-- http://chocolu.net/blog/?p=312 -->
<style lang="scss">
#top{
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  display: inline-block;
  margin: 0 10px;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>