<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/contacts-1-512.png" style="width: 100px;">
    <HelloWorld msg="Welcome to Your Contacts App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "home",
  components: {
    HelloWorld
  }
};
</script>

<style scoped>
.home {
  text-align: center;
}
</style>

