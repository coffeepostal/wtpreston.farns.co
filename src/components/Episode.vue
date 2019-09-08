<template>
  <div class="episode">
    <h1>{{ episodeTitle }}</h1>
    <div class="embed">
      <transition name="loader-fade">
        <Loader v-show="!iframeLoaded" />
      </transition>
      <transition name="iframe-fade">
        <iframe
          width="100%"
          height="166"
          scrolling="no"
          frameborder="no"
          allow="autoplay"
          :src="trackSrc"
          @load="load"
          v-show="iframeLoaded"
        ></iframe>
      </transition>
    </div>
    <div class="transcript">
      <p>Download Transcript PDF:</p>
      <p>
        <a :href="pdfLink" target="_blank" rel="noopener noreferrer">
          <font-awesome-icon :icon="['fas', 'file-pdf']" size="lg" />
          {{ pdfFile }}
        </a>
      </p>
    </div>
  </div>
</template>

<script>
import Loader from "@/components/Loader.vue";

export default {
  name: "Episode",
  components: {
    Loader
  },
  props: {
    episodeId: Number,
    episodeTitle: String,
    episodeTrack: String,
    episodeTranscript: String
  },
  data() {
    return {
      iframeLoaded: false
    };
  },
  computed: {
    trackSrc() {
      return `https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/${this.episodeTrack}&color=%23ff5500&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true`;
    },
    pdfFile() {
      return `0${this.episodeId.toString()}-${this.episodeTitle
        .replace(",", "")
        .replace(/\s+/g, "-")
        .toLowerCase()}.pdf`;
    },
    pdfLink() {
      return `files/${this.pdfFile}`;
    }
  },
  methods: {
    load: function() {
      this.iframeLoaded = true;
    }
  }
};
</script>

<style scoped lang="scss">
.loader-fade-enter-active,
.loader-fade-leave-active {
  transition: opacity 0.5s;
}
.loader-fade-enter,
.loader-fade-leave-to {
  opacity: 0;
}
.iframe-fade-enter-active {
  transition: all 2s;
  transition-delay: 0.75s;
}
.iframe-fade-leave-active {
  transition: all 2s;
}
.iframe-fade-enter-to,
.iframe-fade-leave {
  max-height: 170px;
  overflow: hidden;
}
.iframe-fade-enter,
.iframe-fade-leave-to {
  overflow: hidden;
  max-height: 0;
}
h1 {
}

.episode {
  margin: 0 0 30px;
  border: 1px black solid;
  border-radius: 5px;
  padding: 20px;

  .embed {
    min-height: 170px;
  }

  .transcript {
    margin-top: 15px;
  }
}
</style>