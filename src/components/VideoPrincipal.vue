<template>
  <div class="videoprincipal">
    <q-video
      :ratio="16/9"
      :style="{ border: 'none', borderRadius: '10px' }"
      :src="videoSrc"
    />
    <button @click="atualizarIframe">Atualizar Twitch</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      videoSrc: 'https://player.twitch.tv/?channel=baiano&parent=multistream-ten.vercel.app&muted=true'
    }
  },
  methods: {
    atualizarIframe () {
      // Atualizar a URL do iframe
      // Isso adiciona um parâmetro de data atual à URL para forçar a atualização
      const novaSrc = `${this.videoSrc}&${Date.now()}`
      this.videoSrc = novaSrc
    }
  }
}
</script>

<style scoped>
.videoprincipal {
  grid-area: 2 / 1 / 4 / 2;
  width: 100%;
  height: auto;
  max-width: auto;
  padding-left: 10px;
}

@media screen and (max-width: 768px) {
  .videoprincipal {
    grid-area: auto;
  }
}
</style>
