<template>
  <div class="app">
    <div>
      <div class="header">
        <img class="header__logo" src="../img/images-4.jpg"/>
        <h1 class="header__title">Number</h1>
      </div>
      <h2 style="text-align: center">
        Animated number transition & likes counter library for Vue.js<br/>
      </h2>
      <v-number class="v-number-example" :value="number"/>
    </div>
    <div style="margin-top: 100px">
      <p>Likes counter animation example:</p>
      <div class="likes-counter-example">
        <div class="likes-counter-example__likes">
          <i class="material-icons">favorite</i>
          <v-number v-model="likes"></v-number>
          |
          <v-number v-model="likes" :speed="200"></v-number>
          <span> people liked </span>
        </div>
        <div class="likes-counter-example__button" @click="like()">
          <span>Like</span>
        </div>
      </div>
      <div class='my-title'>My Number:</div>
      <v-umberx-counter class='my-number' :value='number' :option='myOption'/>
      <v-umberx-counter class='my-number' :value='likes' :option='myOption'/>
      <p style="margin-top: 60px">Usage:</p>
      <code>
        <div>
          &#60;v-number v-model='someValue'&#62;
          <br>
          &#60;v-umberx-counter class='my-number' :value='number' :option='myOption'&#62;
        </div>
      </code>
      <!-- <input style='margin-top: 15px' type='number' v-model='number' @focus='clearInterval' /> -->
    </div>
    <div style="flex: 1"></div>
  </div>
</template>

<script>
import VNumber from "@/components/VNumber";
import VUmberxCounter from "@/components/Vumberx";

export default {
  components: {
    VUmberxCounter,
    VNumber,
  },

  data() {
    return {
      number: 1,
      likes: 412153,
      isLiked: true,
      intervalSpeed: 2000,
      interval: null,


      myOption: {
        duration: 500,
        characterWidth: 18,
        // addCharacter: ['♪', '€', '£', '$', '¥', ','],
        decimals: 3,
        thousandsSeparatorFlag: true
        // replaceCharacterMap: ['~', '!', '@', '#', '$', '%', '^', '&', '*', '(', ')', 'A', 'b', 'c', 'd', 'e', 'f', 'g']
      },
      timer: -1

    };
  },

  created() {
    this.startInterval();
  },

  methods: {
    startInterval() {
      this.interval = setInterval(() => this.number++, this.intervalSpeed);
    },

    clearInterval() {
      clearInterval(this.interval);
    },

    like() {
      this.likes += 1;
    }
  }
};
</script>

<style lang="scss">
html,
body {
  height: 100%;
  padding: 0;
  margin: 0;
  overflow: hidden;
  background: linear-gradient(
          to bottom,
          #34495e,
          #1e647c,
          #00818f,
          #009e90,
          #41b883
  );
  color: white;
  font-family: "Open Sans", sans-serif;
}

code {
  background: rgba(black, 0.5);
  width: 460px;
  display: block;
  padding: 20px;
  border-radius: 2px;
}

.header {
  display: flex;
  justify-content: center;
  align-items: center;

  &__logo {
    height: 120px;
  }

  &__title {
    font-size: 82px;
    margin-left: 18px;
  }
}

.v-number-example {
  font-size: 100px;
  color: #fcdae4;
}

.app {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  height: 100%;
  padding: 10px;
  box-sizing: border-box;
  align-items: center;
}

input {
  border: none;
  border-radius: 4px;
  padding: 10px;
  font-size: 16px;
  background: rgba(white, 0.5);
  outline: none;
  width: 60px;
}

.likes-counter-example {
  display: flex;
  align-items: center;

  &__likes {
    display: flex;
    margin-right: 30px;
    align-items: center;

    & .material-icons {
      margin-right: 3px;
      color: #ac0d3c;
    }

    & .v-number {
      margin-right: 3px;
      color: #660423;
      font-weight: bold;
    }
  }

  &__button {
    $color: #4267b2;
    display: flex;
    background-color: $color;
    padding: 6px 30px;
    align-items: center;
    border-radius: 6px;
    width: fit-content;
    cursor: pointer;
    transition: all ease-in-out 0.2s;

    &:hover {
      background-color: darken($color, 6);
      box-shadow: 8px 8px rgba(black, 0.5);
      transform: scale(1.04);
    }

    &:active {
      background-color: darken($color, 8);
      transform: scale(1.01);
      box-shadow: 2px 2px rgba(black, 0.5);
    }

    & .material-icons {
      margin-right: 5px;
      font-size: 18px;
    }
  }
}


/**
vumberx counter
 */
.vue-number-counter-wrapper {
  height: 20px;
  .number-unit {
    width: 24px;
    height: 20px;
  }
}

</style>
