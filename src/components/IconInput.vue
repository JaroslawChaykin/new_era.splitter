<template>
  <div class="icon-input">
    <SplitterIcon class="icon" v-if="typeIcon" :type="typeIcon" />
    <input v-model="value"
           @click="setFocusToEnd"
           class="input very-light-grayish-cyan-bg dark-cyan-text"
           :placeholder="placeholder"
           type="text">
  </div>
</template>

<script>
import SplitterIcon from '@/components/SplitterIcon';
export default {
  name: 'IconInput',
  components: {SplitterIcon},
  props: ['cb', 'placeholder', 'typeIcon'],
  data() {
    return {
      value: ''
    }
  },
  methods: {
    setFocusToEnd() {
      let momentValue = this.value
      this.value = ''
      setTimeout(() => {
        this.value = momentValue
      }, 0);
    }
  },
  watch: {
    value() {
      if(this.cb) this.cb(this.value)
    }
  }
};
</script>

<style scoped>
.icon-input {
  width: 100%;
  display: flex;
  position: relative;
}
.icon {
  position: absolute;
  top: calc(50% - 11px);
  left: 15px;
}
.input {
  width: 100%;
  padding: 5px 12px;
  border-radius: 6px;
  border: 2px solid hsl(189, 41%, 97%);
  font-size: 24px;
  text-align: right;
  cursor: pointer;
}
.input:focus {
  border: 2px solid hsl(172, 67%, 45%);
  outline: hsl(172, 67%, 45%);
}
</style>