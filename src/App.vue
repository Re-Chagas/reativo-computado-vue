<script setup>

//importations

import { reactive, computed } from 'vue';

//counters

const counters = reactive({
  firstcounter : 0 ,
  secondcounter : 0,
})

function decrease() {
  if (counters.firstcounter > 0) {
    counters.firstcounter--
  }
}

function decreasetwo() {
  if (counters.secondcounter > 0) {
    counters.secondcounter--
  }
}

//sum counters

const sumcounters = computed(() => {
    return counters.firstcounter + counters.secondcounter >= 10 ? true : false ;
  });


</script>

<template>
  <div class="counters">

    <div class="first-counter">
      <div class="count-number">
        <p>{{ counters.firstcounter }}</p>
      </div>

      <div class="buttons">
        <button @click="counters.firstcounter++">Increase</button>
        <button @click="decrease">Decrease</button>
      </div>
    </div>

    <div class="second-counter">
      <div class="count-number">
        <p>{{ counters.secondcounter }}</p>
      </div>

      <div class="buttons">
        <button @click="counters.secondcounter++">Increase</button>
        <button @click="decreasetwo">Decrease</button>
      </div>
    </div>

  </div>

  <div class="sum-counters-less" v-if="sumcounters">

  </div>  

  <div class="sum-counters-sum" v-else>

  </div>

</template>

<style scoped></style>
