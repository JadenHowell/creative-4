<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/profile">Profile</router-link>
    </div>
    <div class="content">
      <router-view/>
    </div>
    <div class="footer">
      <div class="githublink">Follow to my Github repo <a href="https://github.com/JadenHowell/creative-4">here</a></div>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.content {
  padding: 20px 100px;
  min-height: 400px;
}

/* Footer */
.footer {
  height: 50px;
  background: #e3e3e3;
  padding-top: 30px;
  margin: 0 auto;
  font-size: 16px;
  width: 80%;
}

.githublink{
  text-align: center;
  margin: 0 auto;
}
</style>
