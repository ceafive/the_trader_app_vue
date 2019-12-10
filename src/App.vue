<template>
  <div>
    <Header></Header>
    <component
      :is="mode"
      :mode="mode"
      :firstNumber="firstNumber"
      :secondNumber="secondNumber"
      :operatorIndicator="operatorIndicator"
      :correctAnswer="correctAnswer"
      :shuffledArray="shuffledArray"
      @answer-question="calculateAnswer"
      @next-question="startGame"
    ></component>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from "./components/Header";
import Footer from "./components/Footer";
import Question from "./components/Question";
import Answer from "./components/Answer";

export default {
  beforeMount() {
    this.startGame();
  },

  data() {
    return {
      mode: "",
      firstNumber: "",
      secondNumber: "",
      operatorIndicator: "",
      correctAnswer: "",
      answersArray: [],
      shuffledArray: []
    };
  },

  methods: {
    getRandomArbitrary(min, max) {
      return Math.floor(Math.random() * (max - min) + min);
    },

    generateRandomNumbers() {
      this.mode = "Question";
      this.answersArray = [];
      let firstNumber = this.getRandomArbitrary(1, 101);
      let secondNumber = this.getRandomArbitrary(1, 101);

      this.firstNumber = firstNumber;
      this.secondNumber = secondNumber;

      let operatorIndicator = ["+", "-"];
      this.operatorIndicator =
        operatorIndicator[Math.floor(operatorIndicator.length * Math.random())];
    },

    randomizeAnswersArray() {
      this.answersArray.push(this.getRandomArbitrary(1, 101));
      this.answersArray.push(this.getRandomArbitrary(1, 101));
      this.answersArray.push(this.getRandomArbitrary(1, 101));

      var calculate = {
        "+": function(x, y) {
          return x + y;
        },
        "-": function(x, y) {
          return x - y;
        }
      };

      let correctAnswer = calculate[this.operatorIndicator](
        this.firstNumber,
        this.secondNumber
      );
      this.correctAnswer = correctAnswer;
      this.answersArray.push(this.correctAnswer);

      function shuffle(array) {
        var currentIndex = array.length,
          temporaryValue,
          randomIndex;

        // While there remain elements to shuffle...
        while (0 !== currentIndex) {
          // Pick a remaining element...
          randomIndex = Math.floor(Math.random() * currentIndex);
          currentIndex -= 1;

          // And swap it with the current element.
          temporaryValue = array[currentIndex];
          array[currentIndex] = array[randomIndex];
          array[randomIndex] = temporaryValue;
        }

        return array;
      }

      this.shuffledArray = shuffle(this.answersArray);
    },

    startGame() {
      this.generateRandomNumbers();
      this.randomizeAnswersArray();
    },

    calculateAnswer(answer) {
      console.log(answer);
      console.log(this.correctAnswer);
      if (answer == this.correctAnswer) {
        this.mode = "Answer";
      } else {
        alert("Wrong! Try Again");
      }
    }
  },

  components: {
    Header,
    Footer,
    Question,
    Answer
  }
};
</script>

<style lang=""></style>
