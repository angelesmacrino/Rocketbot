<template>
  <form class="form" @submit="checkForm" autocomplete="off">
    <label for="name">First name</label>
    <input :class="{'error':error.name}" @blur="checkName" v-model="name" type="text" name="name" placeholder="John">
    <label for="surname">Last name</label>
    <input :class="{'error':error.surname}" @blur="checkSurname" v-model="surname" type="text" name="surname" placeholder="Smith">
    <label for="mail">Email</label>
    <input :class="{'error':error.email}" @blur="checkEmail" v-model="email" type="email" name="email" placeholder="email@email.com">
    <input type="submit"> 
  </form>
</template>

<script>
  var ls = require('local-storage');
  export default {
    data() {
      return {
        name: "",
        surname: "",
        email: "",
        error: {
          name: false,
          surname: false,
          email: false
        }
      }
    },  
  methods: {
    checkName() {
      if (this.name) this.error.name = false
      else this.error.name = true
    },
    checkSurname() {
      if (this.surname) this.error.surname = false
      else this.error.surname = true
    },
    checkEmail() {
      if (this.email) this.error.email = false
      else this.error.email = true
    },
    checkForm(e) {
      if (this.name && this.surname && this.email) {
        ls.set("user.name", this.name);
        ls.set("user.surname", this.surname);
        ls.set("user.email", this.email);
        ls.set("User logged", true);
        this.$emit("UserLogged")
        return true
      }
      else {
        this.checkName()
        this.checkSurname()
        this.checkEmail() 
        e.preventDefault();
      }    
    }
  },
  }
</script>

<style>
    .form {
      position: fixed;
      top: 30%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
    .form label {
      display: block;
      margin-top: 10px;
      margin-bottom: 0px;
      font-weight: bold;
    }
    .form input[type="submit"] {
      display:block;
      margin-top:10px;
      border-radius: 10px;
      padding:10px;
      border:none;
      font-weight:bold;
      background: rgb(120, 119, 187);
    }
    .error {
      border-color: red;
    }
</style>