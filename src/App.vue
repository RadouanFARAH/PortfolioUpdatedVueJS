<template>
  <div id="app">
    <div :class="{ displaynone: show }">
      <Loader />
    </div>
    <div id="Header" :class="{ displaynone: !show }">
      <router-link to="/">
        <img src="../src/assets/white.png" class="logo" />
      </router-link>
      <span class="fontBig">
        <router-link to="/Contact" class="items">Contact</router-link>
        <router-link to="/Projects" class="items">Projects</router-link>
        <router-link to="/Skills" class="items">Skills</router-link>
        <router-link to="/about" class="items">About Me</router-link>
      </span>
    </div>
    <router-view :class="{ displaynone: !show }" />
  </div>
</template>
<script>
import Loader from "./views/Loading";
export default {
  beforeCreate() {
    this.show = false;
    setTimeout(() => {
      this.show = true;
    }, 3000);
  },
  components: {
    Loader,
  },
  data() {
    return {
      show: false,
    };
  },
};
</script>

<style lang="scss">
@import url("https://use.fontawesome.com/releases/v5.0.13/css/all.css");

.displaynone {
  display: none;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
}

#Header {
  padding-inline-start: 10px;
  height: 10vh;
  width: 95%;
}

#Header nav {
  color: white;
  min-height: 50px;
  font-family: comfortaa;
}

#Header .logo {
  margin-top: 0.6em;
  float: left;
  width: 50px;
  height: 50px;
}

#Header .items {
  margin-top: 1.4em;
  float: right;
  margin-left: 15px;
  outline: none;
  font-size: 15px;
  color: white;
  text-decoration: none;

  &:hover {
    outline: none;
    color: #ff4d5a;
    text-decoration: none;
  }
  &:focus {
    outline: none;
    color: #ff4d5a;
    text-decoration: none;
  }

  &:active {
    outline: none;
    color: #ff4d5a;
    text-decoration: none;
  }
}
</style>
