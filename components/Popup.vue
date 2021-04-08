<template>
  <div class="popup-wrapper">
    <div class="popup">Popup</div>
  </div>
</template>

<script>
export default {
  name: 'Popup',
}
</script>

<style scoped>
.popup-wrapper {
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100vw;
  background-color: rgba(61, 61, 61, 0.5);
  z-index: 2;
}
.popup {
  width: fit-content;
  height: fit-content;
  border: 1px solid grey;
}
</style>
