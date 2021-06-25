<template>
  <v-container>
    <div class="QuizTop">
      <h1> QuizTop </h1>
      <p v-for="(q, index) in questions" v-bind:key="index">
        <b>{{ index + 1 }}. {{ q.sentence }} </b><br>
        <v-text-field v-model="q.answer" label="Answer here"></v-text-field>
      </p>
      <v-btn block elevation="2" v-on:click="checkAnswer()"> submit </v-btn>
    </div>
  </v-container>
</template>
<script lang="ts">
    import {Component, Vue} from "vue-property-decorator";
    import { quizdata } from "../data/quizdata";
    import { Question } from "../ts/types/question";

    @Component
    export default class QuizTop extends Vue{

      questions: Array<Question> = this.shuffle(quizdata).slice(0, 3);

      checkAnswer(): void {
          alert(
            this.questions.filter(q => q.correctAnswer.find(correct => correct == q.answer)).length + "/" 
              + this.questions.length
          );
      }

      shuffle(a: Array<Question>): Array<Question> {
        for (let i = a.length - 1; i > 0; i--) {
          const j = Math.floor(Math.random() * (i + 1));
          [a[i], a[j]] = [a[j], a[i]];
          }
        return a;
      }
    }
</script>
<style scoped>
h1 {
  text-align: center;
}
.input-box {
  border: solid 2px black;
}
</style>

