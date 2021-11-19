<template>
  <div>
    <div class="nav-item">
      <input
        v-model="choiceAdd"
        @keydown.enter="searchSelection"
        type="text"
        placeholder="Find Movie and TvSeries"
      />
      <button @click="searchSelection">SEARCH</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "NavBar",
  data() {
    return {
      choiceAdd: "",
    };
  },
  methods: {
    searchSelection() {
      this.$emit("choiceAdd", this.choiceAdd);
    },
  },
};
</script>

<style lang="scss">
</style>