<template>
  <div>
    <h3>
      EmailPhoneEntry
    </h3>
    <form v-on:submit.prevent="submitSearch">
      <input v-model.trim="emailOrPhone" placeholder="Email or phone!">
      <button>Search</button>
    </form>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'EmailPhoneEntry',
  props: {
    currentWorkingObject: ''
  },
  data(){
    return{
      emailOrPhone: ''
    }
  },
  methods: {
    submitSearch: function(){
      var searchQuery = this.emailOrPhone;
      if(this.isValidPhone(searchQuery)){
        //var phoneParams = this.formatUrlParams(searchQuery);
        this.getRecovery(searchQuery);
      }
      else if(this.isValidEmail(searchQuery)){
        //var emailParams = this.formatUrlParams(searchQuery);
        this.getRecovery(searchQuery);
      }
    },

    formatUrlParams(payload){
      var params = Object.entries(payload).map(e => e.join('=')).join('&');
      return '?' + params;
    },

    isValidPhone(phoneNumber){
      // eslint-disable-next-line
      var phoneRegex = /^[\+]?[(]?[0-9]{3}[)]?[-\s\.]?[0-9]{3}[-\s\.]?[0-9]{4,6}$/im;
      return phoneRegex.test(phoneNumber);
    },

    isValidEmail(emailAddress){
      // eslint-disable-next-line
      var emailRegex = /^(([^<>()[\]\\.,;:\s@\"]+(\.[^<>()[\]\\.,;:\s@\"]+)*)|(\".+\"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return emailRegex.test(String(emailAddress).toLowerCase());
    },

    getRecovery(contact){
      // eslint-disable-next-line
      console.log('Finding account for' + contact)
      this.$emit('loadNextControl', 
      {
        userId: 1234, contacts:[
        {display: 'b*****2@kent.edu', type: 'email'}, 
        {display: '1*******9', type: 'phone'}
        ]
      }
      );
    }
  }
}
</script>
