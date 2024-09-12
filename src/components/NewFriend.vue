<template>
  <form @submit.prevent="submitFriend">
    <div>
      <label for="name">Name</label>
      <input type="text" v-model="enteredName">
    </div>
   <div>
      <label for="phone">Phone number</label>
      <input type="tel" v-model="enteredPhone">
    </div>
    <div>
      <label for="email">Email</label>
      <input type="email" v-model="enteredEmail">
    </div>
    <div>
      <button>Add contact</button>
    </div>
  </form>
</template>


<script>
  export default {
    emit: [
      'add-contact'
    ],
    data() {
      return {
        enteredName: '',
        enteredPhone: '',
        enteredEmail: ''
      }
    },
    methods: {
      submitFriend() {
        this.$emit('add-contact',
          this.enteredName,
          this.enteredPhone,
          this.enteredEmail
        )
      }
    }
  }
</script>

