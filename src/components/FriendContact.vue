<template>
  <li>
    <h2>{{ name }} {{ isFavorite }}</h2>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone: {{ phoneNumber }}</strong>
      </li>
      <li>
        <strong>Email: {{ emailAddress }}</strong>
      </li>
    </ul>
     <button @click="$emit('delete-friend',id);">
       Delete Friend
    </button>
  </li>
</template>
<script>
export default {

  props: {
    id:{
      type:String,
      required:true
    },
    name:{
        type:String,
        required:true,
    },
    phoneNumber: {
        type:Number,
        required:true,
    },
    emailAddress: {
        type:String,
        required:true,
    },
 

  },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  emits:['delete-friend'],
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
  
  },
};
</script>
