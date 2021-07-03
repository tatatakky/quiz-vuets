<template>
  <!-- <hello-world /> -->
  <quiz-top />
</template>

<script lang="ts">
  import Vue from 'vue'
  // import HelloWorld from '../components/HelloWorld.vue'
  import QuizTop from '../components/QuizTop.vue'

  export default Vue.extend({
    name: 'Home',

    components: {
      // HelloWorld,
      QuizTop,
    },
  })
</script>
