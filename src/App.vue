<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view />
  </div>
</template>



<style lang="css" global>
@import url(https://fonts.googleapis.com/css?family=Dosis);

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
  background: radial-gradient(ellipse at center, #1A0317 0%, #000000 70%);
  background-size: 100%;
}
</style>

