<template>
  <div>
    <h3>
    Reset password.
    </h3>
    Enter new password.
    <input v-model.trim="password" placeholder="12345">
    <br>
    Confirm password.
    <input v-model.trim="confirm" placeholder="12345">
    <br>
    <button v-on:click="setPasswordChangeRequest">Set new password</button>

  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'PasswordReset',
  props: {

  },
  data(){
    return{
      password: '',
      confirm: ''
    }
  },
  computed: {
    passwordsMatch: function(){
      return this.password === this.confirm;
    }
  },
  methods: {
    setPasswordChangeRequest(){
      if(this.passwordsMatch){
        if(this.confirm.length < 6){
          console.log("Password too short!")
        }
        else{
          console.log("Changing password to: " + this.confirm);
        }
      }
      else{
        console.log("Passwords don't match!");
      }
    }
  }
}
</script>
