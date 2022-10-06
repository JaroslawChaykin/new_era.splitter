<template>
  <span class="splitter-icon">
    <img :src="require(`../assets/images/${selectedType()}`)" alt="1">
  </span>
</template>

<script>
export default {
  name: 'SplitterIcon',
  props: ['type'],
  data() {
    return {
      typesIcon: {
        'dollar': 'icon-dollar.svg',
        'person': 'icon-person.svg'
      }
    }
  },
  methods: {
    selectedType() {
      return this.selectedType = this.typesIcon[this.type]
    }
  }
};
</script>

<style scoped>

</style>