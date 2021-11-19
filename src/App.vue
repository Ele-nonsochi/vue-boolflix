<template>
  <div>
    <PageContainer></PageContainer>
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

@import "~font-awesome/css/font-awesome.min.css";

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

</style>
