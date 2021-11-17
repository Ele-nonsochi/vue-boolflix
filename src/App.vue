<template>
  <div>
    <PageContainer />
  </div>
</template>

<script>
//import axios from "axios";
import PageContainer from "./components/PageContainer.vue"

export default {
  name: 'App',
  components: {
    PageContainer,
  }
}
</script>

<style lang="scss">
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
