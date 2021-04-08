<template>
  <div class="popup-wrapper">
    <div class="popup">
      <div class="btn--close" @click="$emit('popupClose')">×</div>
      <form class="popup-form" @submit.prevent="handleSubmit">
        <div class="popup-form-item">
          <label for="email">Email </label>
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
      if (this.validateEmail(this.userEmail)) {
        this.error = ''
        // eslint-disable-next-line no-console
        console.log(this.userEmail)
        this.sendForm()
        this.$emit('popupClose')
        this.clearForm()
      } else {
        this.error = 'Please, enter a valid email'
      }
    },
    clearForm() {
      this.userEmail = ''
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
  border-radius: 8px;
  padding: 2rem 3rem;
  background: #f4f7f8;
}
.btn--close {
  position: absolute;
  top: 0;
  right: 0;
  padding: 0.5rem;
}
.btn--submit {
  margin-top: 1rem;
  padding: 0.5rem;
  width: 100%;
  outline: 0;
  border: none;
  border-radius: 3px;
  background: #7ccfb6;
  font-weight: 600;
}
.btn--submit:hover {
  background-color: #8fe6cc;
}
.popup-form {
  text-align: center;
}
.popup-form label,
.popup-form input {
  display: block;
  margin-bottom: 0.5rem;
  text-align: left;
}
.popup-form label {
  font-size: 1.2rem;
  font-weight: 600;
}
.popup-form input {
  background-color: #e8eeef;
  border: none;
  border-radius: 3px;
  color: #738089;
  font-weight: 600;
  padding: 10px;
  width: 100%;
}
.popup-form input:focus {
  outline: none;
  background: #e4ebef;
}
.popup-form-item {
  position: relative;
  min-height: 80px;
}
.popup-form-error {
  position: absolute;
  bottom: -5px;
  color: red;
  font-size: 0.8rem;
  text-align: left;
  line-height: 1.2;
}
</style>
