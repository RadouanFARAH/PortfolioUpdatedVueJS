<template>
  <div class="loader">
    <img src="../assets/redouane-loader.gif" />
  </div>
</template>
<script>
export default {
  name: "Loader",
};
</script>
<style lang="scss" scoped>
.loader {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: center;
  margin: 0 auto;
}
.loader > img {
  width: 300px;
  height: 300px;
  margin: 0 auto;
}
</style>
