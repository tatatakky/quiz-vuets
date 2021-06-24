<template>
  <v-container>
    <div class="9uiz">
      <h1> {{ title }} </h1>
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
    @Component
    export default class QuizTop extends Vue{
      questions = [
        {"sentence": "What is this ?", "correctAnswer": ["a", "aa"], "answer": ""},
        {"sentence": "What is that ?", "correctAnswer": ["b", "bb"], "answer": ""},
        {"sentence": "What is it ?",   "correctAnswer": ["c", "cc"], "answer": ""},
        {"sentence": "What is it ?",   "correctAnswer": ["c", "cc"], "answer": ""},
      ];
      title: string = "QuizTop";
      checkAnswer(): void {
          alert(
            this.questions.filter(q => q.correctAnswer.find(correct => correct == q.answer)).length + "/" 
              + this.questions.length
          );
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

