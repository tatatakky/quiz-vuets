<template>
  <v-container>
    <div class="QuizTop">

      <h1> Prog Quiz </h1>

      <div class="explanation"> Please check all questions. Enjoy!</div>

      <!-- Show Questions which is select format -->
      <p v-for="(q, index) in questions" :key="index">
        <b> {{ index + 1 }}. {{ q.sentence }} </b><br>
        <v-radio-group v-model="q.answer">
          <v-radio v-for="s in q.select" :key="s" :label="`${s}`" :value="s" color="purple"></v-radio>
        </v-radio-group>
      </p>

      <!-- Button to check answer -->
      <v-btn block elevation="2" color="#B98FE4" type="sumbit" :disabled="allSelected(questions)" @click="checkAnswer()">
        <v-icon left>mdi-arrow-up-bold-box-outline</v-icon>
        submit
      </v-btn>

      <!-- Show Result -->
      <QuizResult :correct_answer_num="correct_answer_number" :question_num="num" />

      <!-- Show Answer -->
      <v-btn block elevation="2" color="#B98FE4" @click="showAnswerClick()">
        <v-icon left>mdi-television</v-icon>
        Show Answer
      </v-btn>
      <div v-if="showed">
        <QuizAnswer :questions="questions" />
      </div>

    </div>
  </v-container>
</template>
<script lang="ts">
    import {Component, Vue} from "vue-property-decorator";

    import { quizdata } from "../data/quizdata";
    import { Question } from "../ts/types/question";

    import QuizResult from "@/components/QuizResult.vue";
    import QuizAnswer from "@/components/QuizAnswer.vue";

    @Component({
      components: {
        QuizResult,
        QuizAnswer
      }
    })
    export default class QuizTop extends Vue{

      // number of questions
      num: number = 3;

      // parameter to judge answer is showed or hidden.
      showed: boolean = false;

      /**
       * the number of correct answer
       * // TODO: This value to do destructive substitution now, bad code
       */
      correct_answer_number: number = 0;

      // list of questions
      questions: Array<Question> = this.shuffle(quizdata).slice(0, this.num);

      // calculate number of correct answer
      checkAnswer(): void {
        this.correct_answer_number = this.questions.filter(q => q.correctAnswer == q.answer).length
      }

      // check all selected
      allSelected(questions: Array<Question>): boolean {
        return questions.map(q => q.answer).includes("")
      }

      // shuffle questions
      shuffle(q: Array<Question>): Array<Question> {
        for (let i = q.length - 1; i > 0; i--) {
          const j = Math.floor(Math.random() * (i + 1));
          [q[i], q[j]] = [q[j], q[i]];
        }
        return q
      }

      // answer is showed or hidden?
      showAnswerClick(): void {
        this.showed = !this.showed
      }

    }
</script>
<style scoped>
h1 {
  text-align: center;
}

.explanation {
  text-align: center;
  margin: 15px;
  font-style: italic;
}

h3 {
  text-align: center;
  margin: 20px;
}
.input-box {
  border: solid 2px black;
}
</style>

