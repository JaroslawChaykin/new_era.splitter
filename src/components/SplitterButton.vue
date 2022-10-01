<template>
  <button class="button"
          @click="cb">{{ text }}
  </button>
</template>

<script>
export default {
  name: 'SplitterButton',
  props: ['text', 'cb']
};
</script>

<style scoped>
.button {
  width: 100%;
  border: none;
  border-radius: 6px;
  padding: 7px;
  font-size: 20px;
  color: white;
  background-color: hsl(183, 100%, 15%);
  transition: 0.2s ease-in-out;
  cursor: pointer;
}

.button:hover {
  background-color: hsl(172, 67%, 45%);
  color: hsl(183, 100%, 15%);
}
</style>