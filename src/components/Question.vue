<template>
  <div
    class="text-center mx-64 mt-10 mb-64 border border-white animated flipInY"
  >
    <h1 class="text-xl p-4 bg-gray-400 text-black">
      What is {{ firstNumber }} {{ operatorIndicator }} {{ secondNumber }}?
    </h1>

    <div class="flex flex-wrap my-4">
      <div
        class="w-1/2 my-4"
        v-for="(answer, index) in shuffledArray"
        :key="index"
      >
        <button
          @click="answerQuestion(answer)"
          class="p-6 bg-green-500 text-xl w-32 focus:outline-none"
        >
          {{ answer }}
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    "firstNumber",
    "secondNumber",
    "operatorIndicator",
    "correctAnswer",
    "shuffledArray",
    "mode"
  ],

  data() {
    return {};
  },
  methods: {
    answerQuestion(answer) {
      this.$emit("answer-question", answer);
    }
  },
  computed: {}
};
</script>
