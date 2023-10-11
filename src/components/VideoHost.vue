<template>
  <div class="videohost">
    <q-video
      :ratio="16/9"
      src="https://player.twitch.tv/?channel=daniels&parent=embed.example.com&muted=true" frameborder="0" allowfullscreen="true" scrolling="no" height="378" width="620"
    />
  </div>
</template>

<script>
export default {
  // Adicione opções específicas se necessário
}
</script>

<style scoped>
.videohost {
  grid-area: 2 / 2 / 4 / 3;
  width: 100%; /* Largura total em telas menores */
  height: auto; /* Altura automática para ajustar o conteúdo */
}

/* Estilo para telas menores */
@media screen and (max-width: 768px) {
  .videohost {
    grid-area: auto; /* Reverta para fluxo automático na grade */
  }
}
</style>
