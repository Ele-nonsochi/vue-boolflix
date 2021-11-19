<template>
  <div class="container_page">
    <LayoutCard></LayoutCard>
  </div>
</template>

<script>
import LayoutCard from "./LayoutCard.vue";

export default {
  name: "PageContainer",
  components: {
    LayoutCard,
  },
};
</script>

<style lang="scss">
.container_page {
  width: 100%;
  height: 100vh;
}
</style>