<template>
  <div id="demo">
    <div class='my-wrapper'>
      <div class='my-title'>My Number:</div>
      <v-umberx-counter class='my-number' :value='myNumber' :option='myOption'/>
      <!-- <v-umberx-counter class='my-number' :value="'@!Ad*#~,)'" :option='myOption' /> -->
      <!-- <v-umberx-counter class='my-number' :value="17842.7129" :option='myOption' /> -->
    </div>
  </div>
</template>
<script>

import Vumberx from "@/components/Vumberx";
export default {
  name: 'democountertry',
  comments:{Vumberx},
  data() {
    return {
      myNumber: 1999,
      myOption: {
        duration: 2000,
        characterWidth: 18,
        // addCharacter: ['♪', '€', '£', '$', '¥', ','],
        decimals: 3,
        thousandsSeparatorFlag: true
        // replaceCharacterMap: ['~', '!', '@', '#', '$', '%', '^', '&', '*', '(', ')', 'A', 'b', 'c', 'd', 'e', 'f', 'g']
      },
      timer: -1
    }
  },
  methods: {
    getNumber() {
      // this.myNumber = +(Math.random() * 100000).toFixed(0);
      let sign = Math.random() - 0.5 > 0 ? '+' : '-';
      this.myNumber = sign + (Math.random() * 50000).toFixed(2);
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.getNumber();
      this.timer = setInterval(() => {
        this.getNumber();
      }, 6000);
    });
  },
  components: {},
  beforeDestroy() {
    clearInterval(this.timer);
  }
}
</script>
