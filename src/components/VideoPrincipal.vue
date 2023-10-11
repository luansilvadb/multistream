<template>
  <div class="videoprincipal">
    <q-video
      :ratio="16/9"
      :style="{ border: 'none', borderRadius: '10px' }"
      :src="videoSrc"
    />
    <q-btn :loading="loading[3]" color="primary" @click="atualizarIframe" style="width: 150px">
      Button
      <template v-slot:loading>
        <q-spinner-hourglass :class="{ 'on-left': loading[3] }" />
        Loading...
      </template>
    </q-btn>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const loading = ref([false, false, false, false, false, false])

    function simulateProgress (number) {
      // Definimos o estado de carregamento
      loading.value[number] = true

      // Simulamos um atraso
      setTimeout(() => {
        // Terminamos, redefinimos o estado de carregamento
        loading.value[number] = false
      }, 3000)
    }

    return {
      loading,
      simulateProgress
    }
  },

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
