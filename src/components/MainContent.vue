<template>
  <section class="container">
    <div class="album-container row py-3 d-flex justify-content-center">
      <div class="col-3">
        <div
          v-for="(item, index) in albumList"
          :key="index"
          class="card justify-content-center align-items-center"
        >
          <img class="img-fluid" :src="item.poster" :alt="item.title" />
          <div class="title-card">{{ item.title }}</div>
          <div class="text-card">{{ item.author }}</div>
          <div class="text-card">{{ item.genre }}</div>
          <div class="text-card">{{ item.year }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from "axios";
export default {
  name: "MainContent",
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
  .card {
    background: $bg-card-color;
    text-transform: uppercase;
    height: 500px;
    img {
      width: 100%;
      height: auto;
    }
    .title-card {
      color: $title-color;
      font-weight: bold;
    }
    .text-card {
      color: $text-color;
    }
  }
}
</style>
