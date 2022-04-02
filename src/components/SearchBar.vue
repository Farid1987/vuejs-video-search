<template>
  <div class="search-wrapper">
    <form
      @submit.prevent="onSubmit"
      class="w-100 d-flex justify-content-center"
    >
      <input type="text" @input="onInput" class="form-control me-2" />
      <button type="submit" class="btn btn-primary">Search</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      searchValue: "",
    };
  },
  methods: {
    onSubmit() {
      this.$emit("termChange", this.searchValue);
    },
    onInput(e) {
      this.searchValue = e.target.value;
    },
  },
};
</script>

<style lang="scss" scoped>
.search-wrapper {
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  border-top: 1px solid rgba(0, 0, 0, 0.1);
  padding: 10px 0;
  margin-bottom: 20px;
  input {
    max-width: 570px;
  }
}
</style>