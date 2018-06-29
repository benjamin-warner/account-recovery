<template>
  <div>
    <h3>
      Verify the code.
    </h3>
    <input placeholder="12345">
    <button v-on:click="checkCode">Verify</button>
    <br>
    <button v-on:click="back">back</button>
  </div>
</template>

<script>
export default {
  name: 'CodeVerification',
  props: {

  },
  methods: {
    checkCode(){
      this.$emit('loadNextControl');
    },
    back(){
      this.$emit('loadPreviousControl', 
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
