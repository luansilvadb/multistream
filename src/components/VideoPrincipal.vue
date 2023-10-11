<template>
  <div class="videoprincipal">
    <q-video
      :ratio="16/9"
      src="https://www.youtube.com/embed/7_syiuTRfvk?si=zBun4GxnmxAwGATE"
    />
  </div>
</template>

<script>
export default {
  // Adicione opções específicas se necessário
}
</script>

<style scoped>
.videoprincipal {
  grid-area: 2 / 1 / 4 / 2;
  width: 100%; /* Largura total em telas menores */
  height: auto; /* Altura automática para ajustar o conteúdo */
  max-width: 1172px;
}

/* Estilo para telas menores */
@media screen and (max-width: 768px) {
  .videoprincipal {
    grid-area: auto; /* Reverta para fluxo automático na grade */
  }
}
</style>
