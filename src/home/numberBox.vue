<template>
  <div>
    <div class="mui-numbox" data-numbox-min="1" :data-numbox-max="max">
      <!-- "-"按钮，点击可减小当前数值 -->
      <button class="mui-btn mui-numbox-btn-minus" type="button">-</button>
      <input @change="getVlue" class="mui-numbox-input" type="number" value="1" ref="numbers">
      <!-- "+"按钮，点击可增大当前数值 -->
      <button class="mui-btn mui-numbox-btn-plus" type="button">+</button>
    </div>
  </div>
</template>

<script>
import mui from "../lib/Mui/js/mui.min.js";
export default {
  data() {
    return {
      counts: ""
    };
  },
  mounted() {
    mui(".mui-numbox").numbox();
    console.log(this.max + "123");
  },
  methods: {
    getVlue() {
      this.$emit("getCount", parseInt(this.$refs.numbers.value));
    }
  },
  props: ["max"],
  watch: {
    max: function(nval, oval) {
      mui(".mui-numbox")
        .numbox()
        .setOption("max", nval);
    }
  }
};
</script>

<style lang="scss" scoped>
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none !important;
}
input[type="number"] {
  -moz-appearance: textfield;
}
</style>
