<template>
  <div class="selector">
    <select @change="startFilter" v-model="key" name="">
      <option value="All">All</option>
      <option v-for="(genre, index) in genres" :value="genre" :key="index">
        {{ genre }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  // mounted() {
  //   console.log(this.discs[0].genre);
  // },
  name: "FilterComp",
  props: {
    discs: Array,
  },
  data() {
    return {
      key: "All",
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
      this.$emit("startFilter", this.key);
    },
  },
};
</script>

<style lang="scss">
@import "@/assets/vars.scss";
@import "@/assets/general.scss";

.selector {
  margin-top: 10px;

  padding-bottom: 10px;
}
</style>
