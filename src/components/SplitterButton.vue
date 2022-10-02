<template>
  <button class="button"
          :class="[variant ? `${variant}-btn` : 'default-btn']"
          @click="cb"
  >
    {{ text }}
  </button>
</template>

<script>
export default {
  name: 'SplitterButton',
  props: ['text', 'cb', 'variant']
};
</script>

<style scoped>
.button {
  width: 100%;
  border: none;
  border-radius: 6px;
  padding: 7px;
  font-size: 20px;
  transition: 0.2s ease-in-out;
  cursor: pointer;
}
.default-btn {
  color: white;
  background-color: hsl(183, 100%, 15%);
}
.strong-btn {
  color: hsl(183, 100%, 15%);
  background-color: hsl(172, 67%, 45%);
}

.button:hover {
  background-color: hsl(172, 67%, 45%);
  color: hsl(183, 100%, 15%);
}
</style>