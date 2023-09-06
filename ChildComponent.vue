<template>
    <div>
      <p>User Name: {{ user.name }}</p>
      <p>User Age: {{ user.age }}</p>
  
      <!-- Button that emits a custom event -->
      <button @click="emitCustomEvent">Emit Custom Event</button>

      <!-- Use a slot to allow content from the parent component -->
    <slot></slot>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      user: {
        type: Object,
        required: true,
      },
    },
    methods: {
      // Method to emit a custom event
      emitCustomEvent() {
        this.$emit('custom-event', 'Custom event data');
      },
    },
  };
  </script>
  