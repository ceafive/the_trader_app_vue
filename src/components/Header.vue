<template>
  <div class="bg-gray-100 mx-56 mt-4">
    <div class="flex flex-wrap justify-between items-center ">
      <div class="cursor-pointer">
        <router-link to="/" class="lg:inline-block my-2 lg:mx-12 p-2 font-black"
          >Stock Trader
        </router-link>
        <router-link
          to="/portfolio"
          active-class="bg-appBlue1 text-white"
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
        <router-link to="" class="lg:inline-block my-2 lg:mr-1 p-2 "
          >End Day
        </router-link>
        <router-link to="" class="lg:inline-block my-2 lg:mr-1 p-2">
          Save Data
        </router-link>
        <router-link to="" class="lg:inline-block my-2 lg:mr-1 p-2">
          Load Data
        </router-link>
      </div>
    </div>
  </div>
</template>
