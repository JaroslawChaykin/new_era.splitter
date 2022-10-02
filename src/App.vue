<template>
  <section class="splitter-container light-grayish-cyan-bg">
    <div class="splitter-box">
      <splitter-calculator/>
      <splitter-total/>
    </div>
  </section>
</template>

<script>

import SplitterCalculator from '@/components/SplitterCalculator';
import SplitterTotal from '@/components/SplitterTotal';
export default {
  name: 'App',
  components: {SplitterTotal, SplitterCalculator}
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
