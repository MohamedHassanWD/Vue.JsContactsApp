<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>This is the homepage of the application and it intentioally left empty</p>
    <p>
      <em>
        To go to the contacts page
        <router-link to="contacts">Click Here</router-link>
      </em>
    </p>
    <p>
      This Contacts App is built using the beautiful
      <span class="standout">Vue.js</span> Framework.
    </p>
    <h3>
      This App is created By:
      <a
        href="https://github.com/MohamedHassanWD"
        target="_blank"
      >Mohamed Hassan</a>
    </h3>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.standout {
  background: #42b983;
  color: #fff;
  padding: 0 5px;
}
</style>
