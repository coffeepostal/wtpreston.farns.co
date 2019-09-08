<template>
  <div id="logo">
    <transition name="logo-fade" appear>
      <div class="logo-container">
        <img
          id="logo"
          src="@/assets/logo-adventures-on-the-wtpreston.svg"
          alt="Adventures on the W. T. Preston"
        />
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "SVGLogo",
  data() {
    return {
      show: true
    };
  }
};
</script>

<style scoped lang="scss">
.logo-fade-enter-active,
.logo-fade-leave-active {
  transition: opacity 3s;
}
.logo-fade-enter,
.logo-fade-leave-to {
  opacity: 0;
}

#logo {
  display: flex;
  justify-content: flex-end;
  width: 100%;
  .logo-container {
    width: 65%;
    // margin: 0 auto;
    display: block;
    margin: 100px 20px 0;

    img {
      width: 100%;
      height: auto;
    }
  }
}
</style>
