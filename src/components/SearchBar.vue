<template>
  <form class="searchForm" @submit.prevent="handleSubmit">
    <input
      class="searchInput"
      type="text"
      placeholder="Ara..."
      v-model="searchInput"
    />
    <button class="searchBtn" type="submit">Ara</button>
  </form>
</template>

<script>
export default {
  name: "SearchBar",
  emits: ["searchValue"],
  data() {
    return {
      searchInput: "",
    };
  },

  methods: {
    handleSubmit() {
      this.$emit("searchValue", this.searchInput, this.video);
      this.searchInput = "";
    },
  },
};
</script>

<style scoped>
.searchForm {
  width: 100%;
  display: flex;
}
.searchInput {
  width: 85%;
  padding: 15px;
  border-radius: 20px;
  margin-right: 20px;
  font-size: 18px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
.searchBtn {
  width: 15%;
  border: none;
  font-size: 18px;
  border-radius: 20px;
  background-color: red;
  color: white;
  cursor: pointer;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
button:hover {
  background-color: darkred;
}
</style>
