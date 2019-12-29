<template>
  <div class="w-1/3 border border-gray-500 my-2 rounded-lg shadow">
    <div class="bg-appBlue1 text-white p-4 rounded-t-lg">
      <h3>
        {{ stock.name }} <span class="text-xs">(Price: {{ stock.price }})</span>
      </h3>
    </div>
    <div class="flex items-center p-2">
      <input
        class="appearance-none bg-transparent border border-gray-500 w-1/2 text-gray-700 mr-32 p-2 rounded focus:outline-none"
        type="number"
        placeholder="Quantity"
        v-model="quantity"
      />
      <button
        class="flex-shrink-0 bg-appBlue1 hover:bg-appBlue2 py-2 px-4 rounded text-white focus:outline-none"
        @click="buyStock"
        :disabled="quantity <= 0"
      >
        Buy
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["stock"],
  data() {
    return {
      quantity: 0
    };
  },
  methods: {
    buyStock() {
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      };

      this.$store.dispatch("buyStock", order);
      this.quantity = 0;
    }
  }
};
</script>
