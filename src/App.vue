<template>
  <section class="splitter-container light-grayish-cyan-bg">
    <div class="splitter-box">
      <splitter-calculator :appendBillValue="billValue"
                           :appendPeopleValue="peopleValue"
                           :appendTipValue="tipValue"/>
      <splitter-total :total="calcTotal" :amount="calcAmount"/>
    </div>
  </section>
</template>

<script>

import SplitterCalculator from '@/components/SplitterCalculator';
import SplitterTotal from '@/components/SplitterTotal';

export default {
  name: 'App',
  components: {SplitterTotal, SplitterCalculator},
  data() {
    return {
      bill: 0,
      people: 0,
      tip: 0
    }
  },
  computed: {
    calcTotal() {
      if(this.bill && this.people) {
        return ((this.bill / this.people) + this.calcAmount)
      }
      return 0
    },
    calcAmount() {
      return ((this.bill / 100) * this.tip)
    }
  },
  methods: {
    billValue(value) {
      this.bill = value
    },
    peopleValue(value) {
      this.people = value
    },
    tipValue(value) {
      this.tip = value
    },
    reset() {
      this.bill = 0
      this.people = 0
      this.tip = 0
    }
  }
};
</script>

<style>
@import './assets/colors.css';

@font-face {
  font-family: "SpaceMono-Bold";
  src: local("SpaceMono-Bold"),
  url(./assets/fonts/SpaceMono-Bold.ttf) format("truetype");
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: SpaceMono-Bold, sans-serif
}

.splitter-container {
  width: 100%;
  height: 100vh;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}

.splitter-box {
  display: flex;
  background: white;
  padding: 25px;
  border-radius: 20px;
  width: 80%;
}
</style>
