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
export default {
  data: function () {
    return {
      foreground: "#ffffff",
      background: "#000000"
    }
  },
  watch: {
    foregroundColor: function () {
      this.foreground = this.$props.foregroundColor;
    },
    backgroundColor: function () {
      this.background = this.$props.backgroundColor;
    }
  }
}
</script>

<template>
  <div class="preview-box" :style="{'background-color': background, 'color': foreground}">
    <p>Do not go gentle into that good night,</p>
    <p>Old age should burn and rave at close of day;</p>
    <p>Rage, rage against the dying of the light.</p>
    <p>Though wise men at their end know dark is right,</p>
    <p>Because their words had forked no lightning they</p>
    <p>Do not go gentle into that good night.</p>
  </div>
</template>

<style scoped>
.preview-box {
  width: 100%;
  padding: 30px;
  font-size: 1.2rem;
  line-height: 2.8vw;
  border-radius: 1.8vw;
  box-shadow: rgba(0, 0, 0, 0.3) 0px 10px 36px 0px, rgba(0, 0, 0, 0.2) 0px 0px 0px 1px;
  border: 0px;
  outline: 0px;
}
</style>
