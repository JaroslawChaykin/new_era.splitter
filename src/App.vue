<template>
  <section class="splitter-container light-grayish-cyan-bg">
    <div class="splitter-box">
      <splitter-calculator :bill="bill"
                           :changeBill="changeBill"
                           :people="people"
                           :changePeople="changePeople"
                           :tip="tip"
                           :changeTip="changeTip"

      />
      <splitter-total :total="calcTotal" :amount="calcAmount" :reset="reset"/>
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
    };
  },
  computed: {
    calcAmount() {
      return ((this.bill / 100) * this.tip);
    },
    sumOfBillAndAmount() {
      return +this.bill + +this.calcAmount
    },
    calcTotal() {
      if (this.sumOfBillAndAmount && this.people) {
        return this.sumOfBillAndAmount / this.people;
      }
      return 0;
    },

  },
  methods: {
    changeBill(value) {
      this.bill = value;
    },
    changePeople(value) {
      this.people = value;
    },
    changeTip(value) {
      this.tip = value;
    },
    reset() {
      this.bill = 0;
      this.people = 0;
      this.tip = 0;
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
