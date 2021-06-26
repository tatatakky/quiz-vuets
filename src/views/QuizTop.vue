<template>
  <v-container>
    <div class="QuizTop">
      <h1> QuizTop </h1>
      <p v-for="(q, index) in questions" v-bind:key="index">
        <b>{{ index + 1 }}. {{ q.sentence }} </b><br>
        <v-radio-group v-model="q.answer">
          <v-radio v-for="s in q.select" :key="s" :label="`${s}`" :value="s"></v-radio>
        </v-radio-group>
      </p>
      <v-btn block elevation="2" type="sumbit" :disabled="allSelected(questions)" v-on:click="checkAnswer()"> submit </v-btn>
    </div>
  </v-container>
</template>
<script lang="ts">
    import {Component, Vue} from "vue-property-decorator";
    import { quizdata } from "../data/quizdata";
    import { Question } from "../ts/types/question";

    @Component
    export default class QuizTop extends Vue{

      // 表示する問題数
      num: number = 3;

      // 問題のリスト
      questions: Array<Question> = this.shuffle(quizdata).slice(0, this.num);

      // 答え合わせ
      checkAnswer(): void {
          alert(
            this.questions.filter(q => q.correctAnswer.find(correct => correct == q.answer)).length + "/" 
              + this.questions.length
          );
      }

      allSelected(questions: Array<Question>): boolean {
        return questions.map(q => q.answer).includes("")
      }

      // 問題のシャッフル
      shuffle(q: Array<Question>): Array<Question> {
        for (let i = q.length - 1; i > 0; i--) {
          const j = Math.floor(Math.random() * (i + 1));
          [q[i], q[j]] = [q[j], q[i]];
        }
        return q
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

