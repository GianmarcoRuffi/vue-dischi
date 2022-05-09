<template>
  <section class="container">
    <div><FilterComp /></div>
    <div class="album-container row py-3 d-flex justify-content-center">
      <div
        v-for="(item, index) in albumList"
        :key="index"
        class="col-3 card justify-content-center align-items-center"
      >
        <img class="img-fluid" :src="item.poster" :alt="item.title" />
        <div class="title-card">{{ item.title }}</div>
        <div class="text-card">{{ item.author }}</div>
        <div class="text-card">{{ item.genre }}</div>
        <div class="text-card">{{ item.year }}</div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from "axios";
import FilterComp from "./FilterComp.vue";
export default {
  name: "MainContent",
  components: { FilterComp },
  data() {
    return {
      albumList: [],
      apiPath: "https://flynn.boolean.careers/exercises/api/array/",
    };
  },

  mounted() {
    axios
      .get(this.apiPath + "music")
      .then((res) => {
        console.log(res);
        this.albumList = res.data.response;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style lang="scss" scope>
@import "@/assets/vars.scss";
.album-container {
  background: $bg-color;
  width: 100%;
  padding-top: 30px;
  .card {
    background: $bg-card-color;
    text-transform: uppercase;
    height: 450px;
    margin-right: 30px;
    margin-top: 30px;
    width: 20%;

    img {
      width: 100%;
      height: auto;
    }
    .title-card {
      color: $title-color;
      padding-top: 8px;
      font-weight: bold;
    }
    .text-card {
      color: $text-color;
      padding-top: 5px;
    }
  }
}
</style>
