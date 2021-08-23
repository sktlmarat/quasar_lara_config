<template>
  <q-page class="flex flex-center">
    <img
      alt="Quasar logo"
      src="~assets/quasar-logo-vertical.svg"
      style="width: 200px; height: 200px"
    >
    <q-btn label="Login" @click="login"></q-btn>
    <q-btn label="Get User" @click="getUser"></q-btn>

  </q-page>
</template>

<script>
import axios from 'axios'

export default {
  name: 'PageIndex',
  mounted() {
    axios.get('http://127.0.0.1:8000/sanctum/csrf-cookie/')
    .then(res => {
      console.log(res)
    })
  },
  methods: {
    login () {
      const form = {
        email: 'luke@gmail.com',
        password: 'secret'
      }
      axios.post('http://127.0.0.1:8000/login', form)
    },
    getUser () {
      axios.get('http://127.0.0.1:8000/api/user/')
        .then(res => {
          alert([res.data])
          console.log(res.data)
        })
    }
  }
}
</script>
