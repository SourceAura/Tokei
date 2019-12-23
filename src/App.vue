<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">
        <vs-icon icon="home" size="small" color="#FFF"></vs-icon>
      </router-link>
      
      <div></div>
      <router-link to="/about">
      <vs-icon icon="info" size="small" color="#FFF"></vs-icon></router-link>
    </div>
    <router-view />
  </div>
</template>

<style lang="css" global>
@import url(https://fonts.googleapis.com/css?family=Dosis);

#nav {
  position: fixed;
  display: block;
  right: 0;
  bottom: 0;
  margin-right: 40px;
  margin-bottom: 40px;
  z-index: 900;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center !important;
  color: whitesmoke;
  margin-top: 60px;
  font-family: "Dosis", cursive !important;
}
body {
  background: #e69620;
  background: radial-gradient(ellipse at center, #1a0317 0%, #000000 70%);
  background-size: 100%;
}
</style>
