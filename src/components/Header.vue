<template>
  <div class="bg-gray-100 lg:mx-56 mt-4">
    <div class="flex flex-wrap justify-between items-center">
      <div class="cursor-pointer">
        <router-link to="/" class="lg:inline-block my-2 lg:mx-12 p-2 font-black"
          >Stock Trader
        </router-link>
        <router-link
          to="/portfolio"
          active-class="bg-appGreen1 text-white"
          class="lg:inline-block my-2 lg:mr-12 p-2"
        >
          Portfolio
        </router-link>
        <router-link
          to="/stocks"
          active-class="bg-appBlue1 text-white"
          class="lg:inline-block my-2 lg:mr-12 p-2"
        >
          Stocks
        </router-link>
      </div>

      <div class="cursor-pointer text-sm">
        <p class="lg:inline-block my-2 lg:mr-1 p-2 " @click="endDay">
          End Day
        </p>
        <p class="lg:inline-block my-2 lg:mr-1 p-2">
          Save Data
        </p>
        <p class="lg:inline-block my-2 lg:mr-1 p-2">
          Load Data
        </p>
        <div class="lg:inline-block lg:mr-1 cursor-auto text-base">
          <p>
            Funds:
            <span class="bg-green-500 text-white px-1">{{
              funds | currency
            }}</span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    funds() {
      return this.$store.getters.funds;
    }
  },
  methods: {
    endDay() {
      this.$store.dispatch("randomizeStocks");
    }
  }
};
</script>
