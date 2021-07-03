<template>
  <v-container>
    <div class="QuizAnswer">
      <h3> Answer </h3>
      <div v-for="(q, index) in questions" v-bind:key="index">
        <div> {{ index + 1 }}. {{ q.sentence }} <br><b> A. {{ q.correctAnswer }} </b></div><br>
      </div>
    </div>
  </v-container>
</template>
<script lang="ts">
    import {Component, Vue, Prop} from "vue-property-decorator";
    import { Question } from '@/ts/types/question';

    @Component
    export default class QuizAnswer extends Vue{
      @Prop() private questions!: Array<Question>;
    }
</script>
<style scoped>
h3 {
  text-align: center;
  margin: 20px;
}
</style>
