<template>
  <div>
    <form class="search" @submit.prevent="search">
      <v-icon class="icon" size="40">mdi-magnify</v-icon>
      <input
        type="search"
        class="box"
        v-model="searchData"
        @input="search"
        placeholder="ค้นหาหนัง, ซีรีส์ "
      />
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchBox",
  data() {
    return {
      searchData: "",
    };
  },
  methods: {
    search() {
      this.$emit("search", this.searchData);
    },
  },
};
</script>

<style lang="scss" scoped>
.search {
  width: 100%;
  background-color: #2c2c2c;
  height: 70px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  border-radius: 10px;
  padding-inline: 1rem;
}
.box {
  color: #fff;
  font-size: 1.2rem;
  padding: 1rem;
  font-weight: 500;
  width: 100%;
  height: 100%;
}
.box::placeholder {
  color: #858585;
  font-size: 1.2rem;
  font-weight: 600;
  justify-content: center;
}

.box:focus {
  outline: 0px;
}

.icon {
  padding-right: 1rem;
}
</style>
