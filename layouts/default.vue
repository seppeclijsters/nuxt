<template>
    <div id="app">
        <NavBar/>
        <nuxt />
    </div>
</template>

<script>
 import NavBar from "~/components/NavBar.vue";
  export default {
    components: {
      NavBar
    },
    head() {
      return {
        titleTemplate: '%s - Real World Events',
        meta: [
          {
            hid: 'description',
            name: 'description',
            content: 'You can create an event in your neighbourhoud'
          }
        ]
      }
    },
  };
</script>
