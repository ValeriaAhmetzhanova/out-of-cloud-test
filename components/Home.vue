<template>
  <div class="home">
    <Popup v-if="popupActive" />
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      popupActive: false,
    }
  },
}
</script>

<style scoped>
.home {
  /*to check scrolling*/
  height: 200vh;
}
</style>
