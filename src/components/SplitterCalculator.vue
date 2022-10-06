<template>
  <div class="splitter-calculator">
    <div class="calc-type bill">
      <h5 class="grayish-cyan-text">Bill</h5>
      <IconInput placeholder="0" typeIcon="dollar" :cb="billValue"/>
    </div>
    <div class="calc-type tip">
      <h5 class="grayish-cyan-text">Select tip %</h5>
      <div class="tips">
        <SplitterButton v-for="tip of tips"
                        :key="tip"
                        :text="`${tip}%`"
                        :variant="selectedTip === tip ? 'strong' : ''"
                        @click="selectTip(tip)"
        />
        <IconInput placeholder="Custom"
                   :cb="selectTip" />
      </div>
    </div>
    <div class="calc-type number-of-people">
      <h5 class="grayish-cyan-text">Number of people</h5>
      <IconInput placeholder="0" typeIcon="person" :cb="peopleValue"/>
    </div>
  </div>
</template>

<script>
import IconInput from '@/components/IconInput';
import SplitterButton from '@/components/SplitterButton';
export default {
  name: 'SplitterCalculator',
  components: {SplitterButton, IconInput},
  props: ['appendBillValue', 'appendPeopleValue', 'appendTipValue'],
  data() {
    return {
      tips: ['5', '10', '15', '25', '50'],
      selectedTip: '',
    }
  },
  methods: {
    billValue(value) {
      this.appendBillValue(value)
    },
    peopleValue(value) {
      this.appendPeopleValue(value)
    },
    selectTip(tip) {
      this.selectedTip = tip
      this.appendTipValue(this.selectedTip)
    },
  }
};
</script>

<style scoped>
.splitter-calculator {
  width: 50%;
  display: flex;
  flex-direction: column;
  gap: 25px;
  padding: 10px 40px 10px 10px;
}
.tips {
  display: flex;
  justify-content: space-between;
  row-gap: 10px;
  flex-wrap: wrap;
}
.tips button,
.tips .icon-input {
  width: 31%;
}
.active {
  background: red;
}
h5 {
  margin-bottom: 10px;
}
</style>