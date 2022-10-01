<template>
  <div>
    <span>
      <img src="" alt="">
    </span>
    <input v-model="value" class="input very-light-grayish-cyan-bg" type="text">
  </div>
</template>

<script>
export default {
  name: 'IconInput',
  props: [],
  data() {
    return {
      value: ''
    }
  },
  methods: {}
};
</script>

<style scoped>
.input {
  width: 100%;
  padding: 5px 12px;
  border: 2px solid hsl(172, 67%, 45%);
  border-radius: 6px;
}
</style>