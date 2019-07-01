<template>
  <div id="app">
    <div id="nav">
      <img src="./assets/logo.png">
      <div class="menu">
      <router-link to="/">Home</router-link> |
      <router-link to="/status">Status</router-link>
      </div>
    </div>
    <transition name="fade">
    <router-view/>
    </transition>
    <div id="footer">
      <div class="menu">
      <router-link to="/">Home</router-link> |
      <router-link to="/status">Status</router-link>
      </div>
      All rights reserved… or not.
      <br>
      <a target="_blank" href="https://pl.linkedin.com/in/weronika-majewska-b5b887183">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/></svg>
      </a>
    </div>
  </div>
</template>

<style lang="scss">
@import "./mediaqueries.sass";
* {
margin: 0;
padding: 0;
scroll-behavior:smooth;
}
#app {
  font-family: 'Comfortaa', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: $font;
}
#nav {
  padding: 20px;
  display: flex;
  align-items: center;
  background-color: $bcg-primary;
  @include section-shadow;
  img{
    width: 50px;
    height: 50px;
    justify-content: flex-start;
    margin-right: auto;
  }
}
#nav a.router-link-exact-active {
  color: #62875E;
  text-decoration: underline;
}
#footer{
  padding: 100px;
  background-color: $bcg-yellow;
  .menu{
    margin-bottom: 20px;
  }
  svg{
    margin-top: 20px;
  }
}
.menu{
  a {
    font-weight: bold;
    color: $nav-green;
    justify-content: flex-end;
    text-decoration: none;
  }
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
