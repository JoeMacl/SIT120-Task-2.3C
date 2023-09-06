<template>
    <div>
      <p>{{ item.text }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      item: Object,
    },
  };
  </script>
  