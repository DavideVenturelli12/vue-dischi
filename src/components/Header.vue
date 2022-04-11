<template>
  <header>
    <img src="../assets/spotify-logo.png" alt="spotify logo" />
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
};
</script>

<style lang="scss" scoped>
header {
  height: 5vh;
  display: flex;
  align-items: center;
  padding: 5px 5px;
  background-color: #2e3a46;
  img {
    width: 40px;
  }
}
</style>