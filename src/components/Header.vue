<template>
  <header class="d-flex justify-content-space-between align-items-center">
    <div class="logo">
      <img
        src="https://grafica-facile.com/wp-content/uploads/2022/01/spotify-logo.png"
        alt="logo"
        class="img-fluid"
      />
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss" scope>
@import "@/assets/vars.scss";
header {
  background-color: #2e3a46;
  height: 70px;
  .logo {
    width: 50px;
    height: 50px;
    margin-left: 30px;
  }
}
</style>
