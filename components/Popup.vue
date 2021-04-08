<template>
  <div class="popup-wrapper">
    <div class="popup">
      <div class="btn--close" @click="$emit('popupClose')">x</div>
      <form class="popup-form" @submit="handleSubmit">
        <div>
          <label for="email">Email: </label>
          <input id="email" v-model="userEmail" type="text" name="email" />
          <div class="popup-form-error">
            {{ error }}
          </div>
        </div>
        <button class="btn--submit" type="submit">Send</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Popup',
  data() {
    return {
      userEmail: '',
      error: '',
    }
  },
  methods: {
    handleSubmit() {
      event.preventDefault()
      if (this.validateEmail(this.userEmail)) {
        this.error = ''
        // eslint-disable-next-line no-console
        console.log(this.userEmail)
        this.sendForm()
        this.$emit('popupClose')
      } else {
        this.error = 'Please, enter a valid email'
      }
    },
    validateEmail(email) {
      const regex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      return regex.test(String(email).toLowerCase())
    },
    sendForm() {
      const getResponse = () =>
        new Promise((resolve, reject) => {
          setTimeout(() => resolve({ text: 'Thank you!' }), 2000)
        })
      getResponse().then((response) => {
        alert(response.text)
      })
    },
  },
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
  position: relative;
  width: fit-content;
  height: fit-content;
  border: 1px solid grey;
  padding: 2rem 3rem;
  background-color: white;
}
.btn--close {
  position: absolute;
  top: 0;
  right: 0;
  padding: 0.5rem;
}
.btn--submit {
  margin-top: 1rem;
}
.popup-form {
  text-align: center;
}
.popup-form-error {
  color: red;
  font-size: 0.8rem;
  padding: 0.2rem;
}
</style>
