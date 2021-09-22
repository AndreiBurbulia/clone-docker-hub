<template>
  <div class="caricamento">
    <i class="fas fa-spinner"></i>
  </div>
</template>



<script>
export default {
  name: "ContentComponent",
};
</script>


<style scoped lang="scss">
.caricamento {
  width: 100%;
  height: 100vh;
  z-index: 1000;
  top: 0;
  background-color: rgba(0, 0, 0, 0.061);
  i {
    margin-top: 5rem;
    font-size: 4rem;
    animation: caricamento 1s linear infinite;
    position: absolute;
  }
}

@keyframes caricamento {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>