<template>
  <ul>
    <li>
      <h2>{{ name }} {{isFavorite ? '(Favorite)' : ''}}</h2>
      <button @click="toggleFavorite">Toggle Favorite</button>
      <button @click="toggleVisibility">{{ contactIsVisible ? 'Hide' : 'Show' }} details</button>
      <ul v-if="contactIsVisible">
        <strong>Phone:</strong>
        <li>{{phoneNumber}}</li>
        <strong>Email:</strong>
        <li>{{emailAddress}}</li>
      </ul>
      <button @click="$emit('delete', id)">Delete Contact</button>
    </li>
  </ul>
</template>


<script>
export default {
  // props: [
  //     'name',
  //     'phoneNumber',
  //     'emailAddress',
  //     'isFavorite'
  // ],
  props: {
    id: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    phoneNumber: {
      type: String,
      required: true
    },
    emailAddress: {
      type: String,
      required: true
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
      // validator: function(value) {
      //   return value === '1' || value === '0';
      // }
    }
  },
  emits: ['toggle-favorite', 'delete'],
  data() {
    return {
      contactIsVisible: false,
    }
  },
  methods: {
    toggleVisibility() {
      this.contactIsVisible = !this.contactIsVisible;
    },
    toggleFavorite() {
      this.$emit('toggle-favorite', this.id);
    }
  }
}
</script>


