<template>
  <div class="loader">
    <div class="spinner"></div>
  </div>
</template>

<script>
export default {
  name: "Loader"
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.loader {
  position: absolute;
  margin-top: 60px;
  left: 50%;
  margin-left: -25px;
  display: flex;
  justify-content: center;
  align-items: center;

  .spinner {
    border: 6px solid rgba(0, 0, 0, 0.25);
    border-top: 6px solid rgba(0, 0, 0, 0.75);
    border-radius: 50%;
    width: 50px;
    height: 50px;
    animation: spin 2s linear infinite;
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
}
</style>
