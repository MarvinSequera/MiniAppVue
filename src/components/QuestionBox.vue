<template>
  <div>
    <b-jumbotron lead="Bootstrap v4 Components for Vue.js 2">
      <template v-slot:lead>{{question.question}}</template>
      <hr class="my-4" />
      <b-list-group>
        <b-list-group-item v-for="(answer,index) in answers" :key="index">{{answer}}</b-list-group-item>
      </b-list-group>
      <b-button class="button" variant="primary">Submit</b-button>
      <b-button class="button" @click="next" variant="success">Next</b-button>
    </b-jumbotron>
  </div>
</template>
<script>
export default {
  props: {
    question: Object,
    next: Function
  },
  computed: {
    answers() {
      let answers = [...this.question.incorrect_answers];
      answers.push(this.question.correct_answer);
      return answers;
    }
  }
};
</script>

<style scoped>
.button {
  margin: 10px 5px;
  width: 80px;
  text-align: center;
}
</style>