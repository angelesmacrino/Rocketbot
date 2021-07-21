<template>
  <div class="userInformation">
      <p><span>First name:</span>  {{name}}</p>
      <p><span>Last name:</span>  {{surname}}</p>
      <p><span>Email:</span>  {{email}}</p>
      <button @click="LogOut">Log Out</button>
  </div>
</template>

<script>
  var ls = require('local-storage');

export default {
    data() {
        return {
            name: "",
            surname: "",
            email: "",
        }
    },
    methods:{
        LogOut() {
            ls.remove('user.name');
            ls.remove('user.surname');
            ls.remove('user.email');
            ls.remove('User logged');
            this.$emit("UserLoggedOut")
        }
    },
    mounted() {
        this.name = ls.get('user.name');
        this.surname = ls.get('user.surname')
        this.email = ls.get('user.email')
    }
}
</script>

<style>
    .userInformation {
        position: fixed;
        top: 30%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
    span {
        font-weight: bold;
    }
    button {
        display:block;
        margin-top:10px;
        border-radius: 10px;
        padding:10px;
        font-weight:bold;
        border:none;
        background: rgb(120, 119, 187);
    }
</style>