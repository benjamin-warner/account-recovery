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
      console.log(this.emailOrPhone);
    }
  }
}
</script>
