<template>
  <div>
    <Form v-if="logged==null" @UserLogged="userLoggedIn" />
    <User v-if="logged==true" @UserLoggedOut="userLoggedOut"/>
  </div>
</template>

<script>
  var ls = require('local-storage');

export default {
  data() {
    return {
      logged: null
    }
  },
  methods: {
    userLoggedIn() {
      this.logged = true
    },
    userLoggedOut() {
      this.logged = null
    }
  },
  created() {
    this.logged = ls.get('User logged');
  }
}
</script>

<style>
body {
  background: #E3DCCC;
  }
</style>
