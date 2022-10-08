<template>
  <div class="splitter-calculator">
    <div class="calc-type bill">
      <div class="title-input">
        <h5 class="grayish-cyan-text">Bill</h5>
        <span v-if="!bill" class="error">Is required</span>
      </div>
      <IconInput placeholder="0"
                 :required="true"
                 typeIcon="dollar"
                 :value="bill"
                 :cb="changeBill"/>
    </div>
    <div class="calc-type tip">
      <h5 class="grayish-cyan-text">Select tip %</h5>
      <div class="tips">
        <SplitterButton v-for="t of tips"
                        :key="t"
                        :text="`${t}%`"
                        :variant="tip === t ? 'strong' : ''"
                        @click="selectTip(t)"
        />
        <IconInput placeholder="Custom"
                   :cb="selectTip" />
      </div>
    </div>
    <div class="calc-type number-of-people">
      <div class="title-input">
        <h5 class="grayish-cyan-text">Number of people</h5>
        <span v-if="!people" class="error">Is required</span>
      </div>
      <IconInput placeholder="0"
                 :required="true"
                 typeIcon="person"
                 :value="people"
                 :cb="changePeople"/>
    </div>
  </div>
</template>

<script>
import IconInput from '@/components/IconInput';
import SplitterButton from '@/components/SplitterButton';
export default {
  name: 'SplitterCalculator',
  components: {SplitterButton, IconInput},
  props: ['bill', 'changeBill', 'people', 'changePeople', 'tip', 'changeTip'],
  data() {
    return {
      tips: ['5', '10', '15', '25', '50'],
    }
  },
  methods: {
    selectTip(tip) {
      this.changeTip(tip)
    },
  },
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
.title-input {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.title-input span {
  font-size: 12px;
  color: red;
}
h5 {
  margin-bottom: 10px;
}
@media (max-width: 768px) {
  .splitter-calculator {
    width: 100%;
    padding: 10px;
  }
}
</style>