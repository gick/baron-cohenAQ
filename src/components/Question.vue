<template>
  <div class="container">
    <div class="questionComplete">
      <p>{{number +1}})</p>
      <p class="question">{{currentQuestion}}</p>
    </div>
    <form class="radiogroup" v-for="(option,index) in options" v-bind:key="index">
      <input class="radiobutton" type="radio" v-model="response" :value="index" name="option" />
      <label>{{option}}</label>
    </form>
  </div>
</template>

<script>
export default {
  components: {},
  name: "Question",
  data() {
    return {
      response: null,
      options: [
        "tout à fait d'accord",
        "plutôt d'accord",
        "plutôt pas d'accord",
        "pas du tout d'accord",
      ],
    };
  },
  watch: {
    response() {
      this.$store.commit({
        type: "setResponse",
        quest: this.number,
        resp: 4 - this.response,
      });
    },
  },
  props: {
    number: Number,
  },
  computed: {
    currentQuestion: function () {
      return this.$store.state.questions[this.number].quest;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input[type="radio"]:checked + label {
  font-weight: bolder;
}

.container {
  display: flex;
  flex-direction: row;
  align-items: center;
}
.questionComplete {
  display: flex;
  flex-direction: row;
  width: 700px;
  text-align: left;
  align-items: center;
}
.question {
  font-family: "roboto";
  font-weight: bolder;
  font-size: large;
  padding: 5px;
}
.radiogroup {
  width: 400px;
  width: 400px;
  font-family: "Roboto";
  font-weight: 500;
}
</style>
