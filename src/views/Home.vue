<template>
  <div class="home">
    <SVGLogo />
    <transition name="ship-fade" appear>
      <div class="ship-image">
        <img src="../assets/burke-illustration-web.svg" alt="W. T. Preston" />
      </div>
    </transition>
    <div class="content">
      <div v-for="episode in episodes" :key="episode.episodeNumber">
        <Episode
          :episodeId="episode.id"
          :episodeTitle="episode.title"
          :episodeTrack="episode.track"
          :episodeTranscript="episode.transcript"
        />
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Episode from "@/components/Episode.vue";
import SVGLogo from "@/components/SVGLogo.vue";
import episodesJson from "@/assets/episodes.json";

export default {
  name: "home",
  data() {
    return {
      episodes: episodesJson
    };
  },
  components: {
    Episode,
    SVGLogo
  }
};
</script>

<style scoped lang="scss">
.ship-fade-enter-active,
.ship-fade-leave-active {
  transition: opacity 3s;
  transition-delay: 2s;
}
.ship-fade-enter,
.ship-fade-leave-to {
  opacity: 0;
}
.ship-image {
  position: absolute;
  top: 110px;
  margin: 0;
  padding: 0;
  width: 95%;
  height: auto;
  z-index: -1;
}
.content {
  max-width: 960px;
  margin: 0 auto;
  margin-top: 10vw;
  padding: 20px;
  background: rgba(255, 255, 255, 0.95);

  @media screen and (max-width: 960px) {
    margin-top: 55vw;
  }
  @media screen and (min-width: 1600px) and (max-width: 1919px) {
    margin-top: 10vw;
  }
  @media screen and (min-width: 1920px) {
    margin-top: 0;
  }
}
</style>
