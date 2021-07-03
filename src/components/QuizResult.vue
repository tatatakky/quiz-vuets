<template>
  <v-container>
    <div class="QuizResult">
      <h3> Score: {{ correct_answer_num }} / {{ question_num }} </h3>
    </div>
  </v-container>
</template>
<script lang="ts">
    import {Component, Vue, Prop} from "vue-property-decorator";

    @Component
    export default class QuizResult extends Vue{
      @Prop() private question_num!: number;
      @Prop() private correct_answer_num!: number;
    }
</script>
<style scoped>
h3 {
  text-align: center;
  margin: 20px;
}
</style>
