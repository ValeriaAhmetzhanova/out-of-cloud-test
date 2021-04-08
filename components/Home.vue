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
  mounted() {
    setTimeout(() => this.togglePopup(), 3000)
  },
  methods: {
    togglePopup() {
      if (this.popupActive) {
        document.body.classList.remove('overflow-hidden')
      } else {
        document.body.classList.add('overflow-hidden')
      }
      this.popupActive = !this.popupActive
    },
  },
}
</script>

<style>
.overflow-hidden {
  overflow: hidden;
}
.home {
  /*to check scrolling*/
  height: 200vh;
}
</style>
