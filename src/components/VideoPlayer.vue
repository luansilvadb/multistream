<template>
  <div class="video-container">
    <video ref="myVideo"></video>
  </div>
</template>

<script>
import Plyr from 'plyr'
import Hls from 'hls.js'

export default {
  props: {
    videoSource: String // Prop for dynamic video source
  },
  mounted () {
    const player = new Plyr(this.$refs.myVideo, {
      controls: [
        'play-large',
        'play',
        'mute',
        'volume',
        'settings',
        'pip',
        'airplay',
        'fullscreen'
      ],
      volume: 0.2
    })

    if (Hls.isSupported()) {
      const hls = new Hls({
        liveDurationInfinity: true
      })
      hls.loadSource(this.videoSource)
      hls.attachMedia(player.media)
    } else if (player.media.canPlayType('application/vnd.apple.mpegurl')) {
      player.media.src = this.videoSource
    }
  }
}
</script>

<style>
@import '~plyr/dist/plyr.css';

.video-container {
  border-top-left-radius: 10px;
  border-bottom-left-radius: 10px;
  overflow: hidden;
}

video {
  width: 100%;
  height: 100%;
}
</style>
