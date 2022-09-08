<template>
  <div class="container">
    <div class="calculator">
      <div class="calculator-inner">
        <div class="calculator-inner-output">
          <h1>=</h1>
          <div class="calculator-inner-output-display">
            <div class="calculator-inner-output-display-miniResult">
              {{ previous || "0" }}
            </div>
            <div class="calculator-inner-output-display-result">
              {{ current || "0" }}
            </div>
          </div>
        </div>
        <div class="calculator-flex">
          <div class="mode" @click="modeToggle" :class="darkDark">
            <div class="mode-toggle">
              <div id="dark-mode" type="checkbox"></div>
            </div>
          </div>
          <img class="calculator-flex-img" src="../svg/time-left-12447.svg" />
        </div>
      </div>
      <div class="calculator-under">
        <div class="calculator-under-left">
          <div class="calculator-under-left-operations">
            <div
              @click="clear"
              class="calculator-under-left-operations-operator"
            >
              AC
            </div>
            <div
              @click="sign"
              class="calculator-under-left-operations-operator"
            >
              +/-
            </div>
            <div
              @click="percent"
              class="calculator-under-left-operations-operator"
            >
              %
            </div>
          </div>
          <div class="calculator-under-left-numbers">
            <div @click="append('1')" class="btn">1</div>
            <div @click="append('2')" class="btn">2</div>
            <div @click="append('3')" class="btn">3</div>
            <div @click="append('4')" class="btn">4</div>
            <div @click="append('5')" class="btn">5</div>
            <div @click="append('6')" class="btn">6</div>
            <div @click="append('7')" class="btn">7</div>
            <div @click="append('8')" class="btn">8</div>
            <div @click="append('9')" class="btn">9</div>
            <div @click="dot" class="btn">.</div>
            <div @click="append('0')" class="btn">0</div>
            <div @click="append(0)" class="btn">00</div>
          </div>
        </div>
        <div class="calculator-under-right">
          <div class="calculator-under-right-operators">
            <div @click="operation('/')" class="buton">÷</div>
            <div @click="operation('×')" class="buton">x</div>
            <div @click="operation('-')" class="buton">-</div>
            <div @click="operation('+')" class="buton">+</div>
            <div @click="equal" class="btn">=</div>
          </div>
        </div>
        <div class="calculator-under-bar"></div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "CalculatorComponent",
  computed: {
    darkDark() {
      return this.darkMode && "darkmode-toggled";
    },
  },
  data() {
    return {
      display: 0,
      previous: "",
      current: "",
      operator: null,
      operatorClicked: false,
      darkMode: false,
    };
  },
  methods: {
    dark() {
      document.querySelector("body").classList.add("dark-mode");
      this.darkMode = true;
      this.$emit("dark");
    },
    light() {
      document.querySelector("body").classList.remove("dark-mode");
      this.darkMode = false;
      this.$emit("light");
    },
    modeToggle() {
      if (
        this.darkMode ||
        document.querySelector("body").classList.contains("dark-mode")
      ) {
        this.light();
      } else {
        this.dark();
      }
    },
    /*
dark mod işlemleri bitti
*/ clear() {
      this.current = "";
      this.operatorClicked = false;
      this.operator = null;
      this.previous = "";
    },
    sign() {
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = "";
        this.operatorClicked = false;
      }
      this.previous = `${this.previous}${number}`;
      this.current = `${this.current}${number}`;
    },
    dot() {
      if (this.current.indexOf(".") === -1) {
        if (!this.current.length) {
          this.append("0");
        }
        this.append(".");
      }
    },
    setPrevious() {
      this.operatorClicked = true;
    },
    operation(sign) {
      if (this.previous.indexOf("=") !== -1) {
        this.previous = this.current;
      }
      if (!this.operatorClicked) {
        this.current = `${this.current}${sign}`;
        this.previous = `${this.previous}${sign}`;
        this.setPrevious();
      }
    },
    equal() {
      this.current = `${eval(this.previous.replace("×", "*"))}`;
      this.previous = `${this.previous}=${eval(
        this.previous.replace("×", "*")
      )}`;
      this.operatorClicked = false;
    },
  },
};
</script>
<style lang="scss" scoped>
  @import "../assets/color.scss";
.container {
  display: flex;
  align-items: center;
  background:$background100;
  max-width: 100%;
  height: 100vh;
}
.calculator {
  position: relative;
  margin: 0 auto;
  width: 423px;
  height: 858px;
  background: linear-gradient(
    166.34deg,
    #fefefe 0%,
    #f9f9f9 12.84%,
    #f3f3f3 32.53%,
    #e5e5e5 100%
  );
  border-radius: 40px;
  &-inner {
    position: absolute;
    width: 100%;
    height: 50%;
    background: $background200;
    box-shadow: 0px -5px 70px rgba(0, 0, 0, 0.1);
    border-radius: 30px;
    &-output {
      display: flex;
      gap: 205px;
      margin-top: 250px;
      margin-left: 70px;
      &-display {
        display: flex;
        flex-direction: column;
        align-items: center;
        overflow: hidden;
        overflow: visible;
        font-size: 40px;
        line-height: 60px;
        color: $color300;
        margin-top: -20px;
        &-miniResult {
          font-weight: 500;
          font-size: 22px;
          line-height: 33px;
          color: $color200;
        }
      }
    }
  }
  &-under {
    position: absolute;
    display: flex;
    gap: 25px;
    width: 100%;
    height: 60%;
    top: 40%;
    border-radius: 30px;
    background: linear-gradient(
      244.38deg,
      #60d8fd 20.14%,
      #98daf7 49.9%,
      #a4c9ff 70.94%
    );
    &-left {
      display: flex;
      flex-direction: column;
      margin-inline-start: 7%;
      margin-top: 30px;
      &-operations {
        display: flex;
        gap: 35px;
        width: 260px;
        height: 60px;
        background: $background300;
        box-shadow: 0px 3px 15px rgba(0, 0, 0, 0.05);
        border-radius: 40px;
        &-operator {
          display: flex;
          align-items: center;
          margin-left: 23px;
          font-size: 26px;
          cursor: pointer;
        }
      }
      &-numbers {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 25px;
        align-items: center;
        text-align: center;
        margin-top: 20px;
      }
    }
    &-right {
      align-items: center;
      text-align: center;
      margin-top: 34px;
      width: 70px;
      height: 430px;
      background: $background300;
      box-shadow: 0px 3px 15px rgba(0, 0, 0, 0.05);
      border-radius: 40px;
      &-operators {
        display: flex;
        flex-direction: column;
        gap: 38px;
        margin-top: 10px;
        font-size: 26px;
        line-height: 50px;
        color: #373737;
        cursor: pointer;
      }
    }
    &-bar {
      position: absolute;
      width: 175px;
      height: 5px;
      left: 124px;
      top: 483px;
      background: $background400;
      border-radius: 25px;
    }
  }
  &-flex {
    display: flex;
    align-items: center;
    margin-top: -480px;
    width: 100%;
    height: 100%;
    margin-left: 154px;
    gap: 60px;
  }
}
.btn {
  display: flex;
  display: block;
  width: 70px;
  height: 70px;
  background: $background300;
  border-radius: 50%;
  font-weight: 600;
  font-size: 26px;
  line-height: 66px;

  color: $color300;
  cursor: pointer;
}
// _dark-mode.scss
.mode {
  position: relative;
  width: 122px;
  height: 44px;
  background: $background500;
  border-radius: 40px;
  overflow: hidden;
  cursor: pointer;
  &-toggle {
    position: absolute;
    top: 0;
    left: 30px;
    bottom: 0;
    margin: auto;
    width: 30px;
    height: 30px;
    border-radius: 50%;
    border: 3px solid transparent;
    box-shadow: inset 0 0 0 2px #a5abba;
    overflow: hidden;
    transition: transform 0.5s ease;
    #dark-mode {
      position: relative;
      width: 100%;
      height: 100%;
      overflow: hidden;
      border-radius: 50%;
      &:before {
        content: "";
        position: relative;
        width: 100%;
        height: 100%;
        left: 50%;
        float: left;
        background-color: $background600;
        transition: border-radius 0.5s ease, width 0.5s ease, height 0.5s ease,
          left 0.5s ease, transform 0.5s ease;
      }
    }
  }
}
body.dark-mode {
  .calculator {
    &-inner {
      background: linear-gradient(
        166.34deg,
        #373737 0%,
        #252628 22.9%,
        #000309 100%
      );
      color: $color100;
      &-display {
        color: $color100;
      }
      &-output {
        &-display {
          &-miniResult {
            color: $color400;
          }
          &-result {
            color: $color100;
          }
        }
      }
    }
    &-under {
      background: linear-gradient(
        244.38deg,
        #2c9abc15 0.14%,
        #2a7da1 2.9%,
        #143260 40.94%,
        #061d57 60.11%
      );
      color: $color100;
      &-bar {
        background: $background700;
      }
      &-left {
        &-operations {
          background: $background800;
        }
      }
      &-right {
        background: $background800;
        &-operators {
          color: $color100;
        }
      }
    }
  }
  .btn {
    color: $color100;
    background: $background800;
  }
  .mode {
    background-color: lighten(#1b6a9c, 5%);
    &-toggle {
      transform: translateX(19px);
      #dark-mode {
        &:before {
          border-radius: 50%;
          width: 150%;
          height: 85%;
          left: 40%;
          transform: translate(-10%, -40%), rotate(-35deg);
        }
      }
    }
  }
}
</style>
