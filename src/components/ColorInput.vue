<script setup>
defineProps({
  label: {
    type: String
  }
})
</script>
<script>
export default {
  data: function () {
    return {
      color: this.$props.label === 'Foreground Color' ? "#ffffff" : "#000000"
    }
  },
  methods: {
  },
  watch: {
    color: function () {
      this.$emit('colorChanged', this.color);
    }
  }
}
</script>

<template>
  <div class='colorInput'>
    <label for="color-input">{{ this.$props.label + ": "}}<span class="color-code">{{this.color.toUpperCase()}}
      </span></label>
    <input id="color-input" type="color" v-model="color" />
  </div>
</template>

<style scoped>
.colorInput {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin-top: 3vw;
  color: rgb(38, 38, 38);
}

.colorInput>label {
  font-weight: 600;
  font-size: 2rem;
}

.colorInput>label>.color-code {
  font-weight: 400;
  letter-spacing: 1px;
}

.colorInput>input {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  width: 50px;
  height: 53px;
  background-color: transparent;
  border: none;
  cursor: pointer;
}

.colorInput>input::-webkit-color-swatch {
  border-radius: 100%;
  border: 2px solid rgba(0, 0, 0, 0.5);
  transition: border 0.2s ease;
  box-shadow: rgba(100, 100, 111, 0.4) 0px 7px 29px 0px;

}

.colorInput>input::-moz-color-swatch {
  border-radius: 100%;
  border: 2px solid rgba(0, 0, 0, 0.5);
}

.colorInput>input::-webkit-color-swatch:hover {
  border: 3px solid rgba(0, 0, 0, 0.5);
}
</style>
