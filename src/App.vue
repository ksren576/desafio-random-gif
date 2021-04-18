<template>
  <div>
    <Nav/>
    <Main/>
  </div>
</template>

<script>

import Nav from "./components/Nav";
import Main from "./components/Main"

export default {
  name: 'App',
  components: {
    Nav,
    Main
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background-color: skyblue;
}
</style>
