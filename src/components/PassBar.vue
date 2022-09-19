<script setup>
defineProps({
  ratio: {
    type: String
  }
})
</script>

<script>
export default {
  data: function () {
    return {
      isPass: true,
    }
  },
  watch: {
    ratio: function () {
      if (this.$props.ratio >= 3) {
        this.isPass = true;
      } else {
        this.isPass = false;
      }
    }
  }
}
</script>

<template>
  <div class="pass-bar" :class="{pass: isPass}">
    {{ isPass ? 'PASS' : 'FAIL'}}
  </div>
</template>

<style scoped>
.pass-bar {
  text-align: center;
  background-color: rgb(180, 54, 54);
  color: rgb(231, 231, 231);
  transition: background-color 0.3s ease;
  border-radius: 1vw;
  margin-top: 20px;
  padding: 1vw 0;
  font-weight: 600;
  font-size: 1.4rem;
  letter-spacing: 3px;
  box-shadow: rgba(0, 0, 0, 0.3) 0px 10px 36px 0px, rgba(0, 0, 0, 0.2) 0px 0px 0px 1px;
}

.pass {
  background-color: rgb(13, 103, 13);
}
</style>
