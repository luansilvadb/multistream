<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="chat">
    <q-video
      :ratio="16/9"
      src="https://www.twitch.tv/embed/daniels/chat?parent=multistream-ten.vercel.app"
    />
  </div>
</template>

<script>
export default {
  // Adicione opções específicas se necessário
}
</script>

<style scoped>
.chat {
  grid-area: 3 / 2 / 4 / 3;
  width: 100%; /* Largura total em telas menores */
  height: auto; /* Altura automática para ajustar o conteúdo */
}

/* Estilo para telas menores */
@media screen and (max-width: 768px) {
  .chat {
    grid-area: auto; /* Reverta para fluxo automático na grade */
  }
}
</style>
