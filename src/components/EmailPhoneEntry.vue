<template>
  <div>
    <form v-on:submit.prevent="submitSearch">
      <input v-model.trim="emailOrPhone" placeholder="Email or phone!">
      <button>Search</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'EmailPhoneEntry',
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
        this.getRecovery();
      }
      else if(this.isValidEmail(searchQuery)){
        //var emailParams = this.formatUrlParams(searchQuery);
        this.getRecovery();
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
      console.log('emitting...' + contact)
      this.$emit('loadVerification')//, {userId: 1234, via: contact});
    }
  }
}
</script>
