<template>
  <div id="app">
    <a-row>
      <a-col span="4"></a-col>
      <a-col span="16">
        <div id="nav">
          <router-link to="/">Home</router-link>&nbsp;|
          <router-link to="/contacts">Contacts</router-link>
        </div>
        <router-view/>
      </a-col>
      <a-col span="4"></a-col>
    </a-row>
  </div>
</template>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  text-align: center;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
