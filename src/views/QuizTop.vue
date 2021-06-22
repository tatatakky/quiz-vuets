<template>
  <div class="quizTop">
    <h1>This is an {{ title }} page</h1>
    <p v-for="(q, index) in questions" v-bind:key="index">
      <b>{{ index + 1 }}. {{ q.sentence }} </b><br>
      <input class="input-box" v-model="q.answer" placeholder="Please answer here!">
    </p>
    <input type="submit" value="Submit" v-on:click="checkAnswer()">
  </div>
</template>
<script lang="ts">
    import {Component, Vue} from "vue-property-decorator";
    @Component
    export default class QuizTop extends Vue{
      questions = [
        {"sentence": "What is this ?", correct: "a", "answer": ""},
        {"sentence": "What is that ?", correct: "b", "answer": ""},
        {"sentence": "What is it ?",   correct: "c", "answer": ""}
      ];
      title: string = "QuizTop";
      checkAnswer(): void {
          alert( this.questions.filter(x => x.answer == x.correct).length + "/" + this.questions.length );
      }
    }
</script>
<style scoped>
.input-box {
  border: solid 2px black;
}
</style>

