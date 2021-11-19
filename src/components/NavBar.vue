<template>
  <div class="nav-item">
    <input
      v-model="choiceAdd"
      @keydown.enter="searchSelection"
      type="text"
      placeholder="Find Movie and TvSeries"
    />
    <button @click="searchSelection">SEARCH</button>
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
.nav-item {
  padding: 4px 10px;
  margin: 0 10px;
  border: 1px solid black;
  border-radius: 5px;
  input {
    padding: 5px 10px;
    margin-right: 10px;
    margin-left: 30px;
    border: 1px solid black;
    border-radius: 5px;
  }
  button {
    padding: 5px 10px;
    border: 1px solid black;
    border-radius: 5px;
    background: red;
    cursor: pointer;
  }
}
</style>