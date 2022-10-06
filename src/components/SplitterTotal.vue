<template>
  <div class="splitter-total dark-cyan-text dark-cyan-bg">
    <div class="total-info">
      <div class="result-info tip-amount">
        <div class="title">
          <h5 class="text light-grayish-cyan-text">Tip amount</h5>
          <h6 class="subtext dark-grayish-cyan-text">/ person</h6>
        </div>
        <div class="result strong-cyan-text">
          ${{ amount.toFixed(2) }}
        </div>
      </div>
      <div class="result-info total">
        <div class="title">
          <h5 class="text light-grayish-cyan-text">Total</h5>
          <h6 class="subtext dark-grayish-cyan-text">/ person</h6>
        </div>
        <div class="result strong-cyan-text">
          ${{ total.toFixed(2) }}
        </div>
      </div>
    </div>
    <SplitterButton text="RESET" variant="strong" :cb="resetValues"/>
  </div>
</template>

<script>
import SplitterButton from '@/components/SplitterButton';

export default {
  name: 'SplitterTotal',
  props: ['total', 'amount', 'reset'],
  components: {SplitterButton},
  methods: {
    resetValues() {
      this.reset()
    }
  }
};
</script>

<style scoped>
.splitter-total {
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  border-radius: 20px;
  padding: 40px 30px;
}

.result-info {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.result {
  font-size: 48px;
}
</style>