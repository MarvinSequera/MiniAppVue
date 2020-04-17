<template>
  <div>
    <b-jumbotron lead="Bootstrap v4 Components for Vue.js 2">
      <template v-slot:lead>{{question.question}}</template>
      <hr class="my-4" />
      <b-list-group>
        <b-list-group-item
          class="list-group"
          v-for="(answer,index) in answers"
          :key="index"
          @click="selectAnswer(index)"
          :class="[selectedIndex === index ? 'selected' : '']"
        >{{answer}}</b-list-group-item>
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
  data() {
    return {
      selectedIndex: null
    };
  },
  computed: {
    answers() {
      let answers = [...this.question.incorrect_answers];
      answers.push(this.question.correct_answer);
      return answers;
    }
  },
  methods: {
    selectAnswer(index) {
      this.selectedIndex = index;
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
.list-group:hover {
  background-color: #eee;
  cursor: pointer;
}
.selected {
  background-color: lightblue;
}
.correct {
  background-color: lightgreen;
}
.incorrect {
  background-color: red;
}
</style>