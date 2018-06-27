<template>
  <div id="app">
    <h1>Account Recovery</h1>
    <component :is="currentControl" v-on:loadVerification="currentControl = 'CodeMethodSelection'"></component>
  </div>
</template>

<script>
import EmailPhoneEntry from './components/EmailPhoneEntry.vue'
import CodeMethodSelection from './components/CodeMethodSelection.vue'
import CodeVerification from './components/CodeVerification.vue'
import PasswordReset from './components/PasswordReset.vue'

export default {
  name: 'app',
  components: {
    EmailPhoneEntry, CodeMethodSelection, 
    CodeVerification, PasswordReset
  },
  data(){
    return{
      currentControl: 'EmailPhoneEntry'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
