<template>
  <div>
    <h3>
    Choose verification code method.
    </h3>
    <div v-for="(contact, index) in currentWorkingObject.contacts" :key="index">
      <a href="#" v-on:click="selectMethod(index)">
        {{ contact.display }}
      </a>
    </div>
    <button v-on:click="sendCode">Send code</button>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'CodeMethodSelection',
  props: {
    currentWorkingObject: ''
  },
  data() {
    return{
      methodIndex: -1
    }
  },
  computed: {
    selectedMethod: function(){
      return this.currentWorkingObject.contacts[this.methodIndex];
    }
  },
  methods: {
    selectMethod(index){
      this.methodIndex = index;
      console.log("Current selection: " + this.selectedMethod.display);
    },

    sendCode(){
      console.log("Sent code to " + this.selectedMethod.display);
      this.$emit('loadNextControl');
    }
  }
}
</script>
