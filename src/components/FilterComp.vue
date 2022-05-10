<template>
  <div class="selector">
    <select @change="startFilter" v-model="key" name="">
      <option value="All">All</option>
      <option v-for="(genre, index) in genres" :value="genre" :key="index">
        {{ genre }}
      </option>
    </select>

    <input type="text" v-model="inputText" @change="startFilter" />
  </div>
</template>

<script>
export default {
  name: "FilterComp",
  props: {
    discs: Array,
  },
  data() {
    return {
      key: "All",
      inputText: "",
    };
  },

  computed: {
    genres() {
      const genreList = [];
      this.discs.forEach((disc) => {
        if (!genreList.includes(disc.genre)) {
          genreList.push(disc.genre);
          console.log(disc.genre);
        }
      });

      console.log(genreList);
      return genreList;
    },
  },

  methods: {
    startFilter() {
      let searchKeys = {
        genre: this.key,
        searchText: this.inputText,
      };
      this.$emit("startFilter", searchKeys);
    },
  },
};
</script>

<style lang="scss">
@import "@/assets/vars.scss";
@import "@/assets/general.scss";

.selector {
  margin-top: 10px;
  padding-bottom: 20px;
  width: 40px;
}
</style>
