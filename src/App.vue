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

  const pairodd = computed(() => {
    if ((counters.firstcounter + counters.secondcounter) % 2 == 0) {
      return true
    }
    return false 
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

    <div class="plus">
      <p>+</p>
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

  <div v-if="sumcounters" class="sum-counters-less" >
    <p>{{counters.firstcounter + counters.secondcounter }}</p>
    <p>O resultado é maior que 10</p>
  </div>  

  <div v-else class="sum-counters-sum" >
    <p>{{counters.firstcounter - counters.secondcounter }}</p>
    <p>O resultado é menor que 10</p>
  </div>

  <div class="pairodd">
    <p>O numero é {{ pairodd ? 'par' : 'ímpar' }}</p>
    <p>{{ pairodd ? 'true' : 'false' }}</p>
  </div>

</template>

<style scoped>

*{
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
  .counters{
    display: flex;
    justify-content: center;
    gap: 20px;
    margin-top: 100px;
  }

  .count-number{
    display: flex;
    justify-content: center;
  }

.sum-counters-less, .sum-counters-sum, .pairodd{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.sum-counters-less, p{
  margin-top: 10px;
}

</style>
