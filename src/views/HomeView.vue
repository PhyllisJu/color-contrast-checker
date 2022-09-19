<script>
import ColorInput from '@/components/ColorInput.vue';
import Preview from '@/components/Preview.vue';
import Result from '@/components/Result.vue';
import PassBar from '@/components/PassBar.vue';

export default {
  components: {
    ColorInput,
    Preview,
    Result,
    PassBar
  },
  data: function () {
    return {
      foreground: "#ffffff",
      background: "#000000",
      ratioVal: "21.00"
    }
  },
  methods: {
  }
}
</script>

<template>
  <div id="app">
    <div class="top">
      <h1>Color Contrast Checker</h1>
    </div>
    <div class="bottom">
      <div class="left">
        <Preview v-bind:foregroundColor="foreground" v-bind:backgroundColor="background" />
        <PassBar v-bind:ratio="ratioVal" />
      </div>
      <div class="right">
        <Result v-bind:foregroundColor="foreground" v-bind:backgroundColor="background"
          v-on:ratioChanged="ratio => ratioVal = ratio" />
        <ColorInput label="Foreground Color" v-on:colorChanged="color => foreground = color" />
        <ColorInput label="Background Color" v-on:colorChanged="color => background = color" />
      </div>
    </div>

  </div>
</template>

<style>
#app>.top {
  background-color: rgb(50, 50, 50);
  color: rgb(231, 231, 231);
  text-align: center;
  width: 100%;
  padding: 3vw 0;
  font-weight: 600;
  font-size: 1.5rem;
  letter-spacing: 1px;
}

#app>.bottom {
  margin-top: 3vw;
  width: 75%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

#app>.bottom>.left {
  width: 50%;
}

#app>.bottom>.right {
  width: 45%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>
