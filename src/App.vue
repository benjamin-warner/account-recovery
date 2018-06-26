<template>
  <component :is="currentControl"></component>
</template>

<script>
import EmailPhoneEntry from './components/EmailPhoneEntry.vue'

export default {
  name: 'app',
  components: {
    EmailPhoneEntry
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
