<template>
  <div id="app">
    <h1>Account Recovery</h1>
    <component :is="currentControl" v-bind:currentWorkingObject="currentWorkingObject"
    v-on:loadNextControl="loadNextControl($event)"
    v-on:loadPreviousControl="loadPreviousControl($event)">
    </component>
  </div>
</template>

<script>
/* eslint-disable */
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
      componentIndex: 0,
      currentControl: 'EmailPhoneEntry',
      currentWorkingObject: ''
    }
  },
  methods:{
    loadNextControl(dataToSend){
      this.componentIndex++;
      this.currentWorkingObject = dataToSend;
      this.loadComponent();
    },
    loadPreviousControl(dataToSend){
      this.componentIndex--;
      this.currentWorkingObject = dataToSend;
      this.loadComponent();
    },
    loadComponent(){
      switch(this.componentIndex){
        case 0: 
          this.currentControl = 'EmailPhoneEntry';
          break;
        case 1: 
          this.currentControl = 'CodeMethodSelection';
          break;
        case 2: 
          this.currentControl = 'CodeVerification';
          break;
        case 3: 
          this.currentControl = 'PasswordReset';
          break;
        default:
          break;
      }
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
