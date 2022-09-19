<script setup>
defineProps({
  foregroundColor: {
    type: String
  },
  backgroundColor: {
    type: String
  }
})
</script>

<script>
import colorContrast from 'color-contrast';
export default {
  data: function () {
    return {
      foreground: "#ffffff",
      background: "#000000",
      ratio: colorContrast("#ffffff", '#000000').toFixed(2),
    }
  },
  watch: {
    foregroundColor: function () {
      this.foreground = this.$props.foregroundColor;
      this.ratio = colorContrast(this.foreground, this.background).toFixed(2);
      this.$emit('ratioChanged', this.ratio);
    },
    backgroundColor: function () {
      this.background = this.$props.backgroundColor;
      this.ratio = colorContrast(this.foreground, this.background).toFixed(2);
      this.$emit('ratioChanged', this.ratio);
    }
  }
}
</script>

<template>
  <div class="result">
    <p><strong>Contrast Ratio: </strong>{{ ratio }}</p>
    <p><strong>WCAG Level: </strong>{{ ratio >= 7
    ? "AAA (Awesome!)"
    : ratio >= 4.5
    ? "AA (Great!)"
    : ratio >= 3
    ? "A(Not Bad)"
    : "You need to improve!"}}</p>
  </div>
</template>

<style scoped>
.result {
  width: 100%;
  font-size: 1.8rem;
  letter-spacing: 1px;
  text-align: left;
  line-height: 7vw;
  color: rgb(38, 38, 38);
}
</style>
