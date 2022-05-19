<template>
  <nav>
    <router-link to="/">Home</router-link>
  </nav>
  <router-view/>
</template>

<script></script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@900&display=swap');
body{
  background-color:#181920;
  font-family: 'Poppins', sans-serif;

}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}

nav {
  padding-bottom: 30px;
  padding-top: 30px;
  width: 100%;


}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
