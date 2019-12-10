<template>
  <div class="text-center mx-64 mt-10 mb-64 bg-green-400 animated flipInY">
    <h1 class="p-10 text-green-900 text-6xl ">Correct!</h1>
    <hr />
    <button
      @click="nextQuestion"
      class="bg-blue-500 hover:bg-blue-700 text-xl p-4 my-4 focus:outline-none font-thin"
    >
      Next Question
    </button>
  </div>
</template>

<script>
export default {
  methods: {
    nextQuestion() {
      this.$emit("next-question");
    }
  }
};
</script>
