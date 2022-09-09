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
          
          <svg class="calculator-flex-img"  xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="30" height="30" viewBox="0 0 256 256" xml:space="preserve">

<defs>
</defs>
<g style="stroke: none; stroke-width: 0; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10;   opacity: 1;" transform="translate(1.4065934065934016 1.4065934065934016) scale(2.81 2.81)" >
	<path d="M 44.993 90 c -3.887 0 -7.835 -0.537 -11.753 -1.667 C 10.733 81.841 -2.297 58.25 4.193 35.744 c 3.144 -10.903 10.345 -19.929 20.278 -25.416 c 9.933 -5.487 21.407 -6.778 32.31 -3.632 c 1.592 0.459 2.511 2.122 2.052 3.714 c -0.459 1.592 -2.121 2.51 -3.714 2.051 c -9.364 -2.699 -19.217 -1.592 -27.747 3.119 S 12.658 28.043 9.958 37.406 c -5.574 19.327 5.617 39.587 24.945 45.161 c 19.327 5.574 39.587 -5.618 45.161 -24.945 c 0.459 -1.592 2.12 -2.512 3.714 -2.052 c 1.592 0.459 2.511 2.122 2.052 3.714 C 80.468 77.874 63.439 90 44.993 90 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" />
	<path d="M 64.588 16.22 c -0.506 0 -1.02 -0.128 -1.49 -0.398 l -0.398 -0.224 c -1.45 -0.802 -1.975 -2.628 -1.173 -4.078 c 0.803 -1.449 2.628 -1.976 4.077 -1.172 l 0.48 0.27 c 1.438 0.825 1.934 2.658 1.108 4.095 C 66.638 15.679 65.628 16.22 64.588 16.22 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10;  opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" />
	<path d="M 83.579 42.048 c -1.38 0 -2.621 -0.957 -2.928 -2.36 c -0.065 -0.299 -0.136 -0.597 -0.209 -0.893 c -0.398 -1.608 0.582 -3.235 2.191 -3.634 c 1.612 -0.398 3.235 0.583 3.634 2.191 c 0.087 0.35 0.169 0.701 0.246 1.054 c 0.354 1.619 -0.672 3.218 -2.29 3.571 C 84.007 42.025 83.791 42.048 83.579 42.048 z M 79.762 31.77 c -1.068 0 -2.102 -0.571 -2.644 -1.577 c -0.146 -0.27 -0.295 -0.538 -0.447 -0.804 c -0.825 -1.437 -0.329 -3.271 1.107 -4.096 c 1.436 -0.825 3.271 -0.33 4.096 1.107 c 0.18 0.313 0.355 0.627 0.525 0.944 c 0.786 1.459 0.241 3.279 -1.217 4.065 C 80.73 31.654 80.243 31.77 79.762 31.77 z M 73.268 22.931 c -0.782 0 -1.564 -0.304 -2.151 -0.91 c -0.214 -0.219 -0.429 -0.435 -0.648 -0.649 c -1.188 -1.155 -1.213 -3.055 -0.057 -4.242 c 1.155 -1.188 3.056 -1.213 4.242 -0.057 c 0.259 0.252 0.515 0.508 0.766 0.767 c 1.155 1.189 1.127 3.088 -0.061 4.242 C 74.776 22.649 74.022 22.931 73.268 22.931 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10; fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" />
	<path d="M 84.455 52.48 c -0.054 0 -0.107 -0.001 -0.161 -0.004 c -1.655 -0.088 -2.925 -1.5 -2.838 -3.154 l 0.021 -0.446 c 0.058 -1.657 1.442 -2.969 3.104 -2.893 c 1.656 0.059 2.951 1.448 2.893 3.104 l -0.024 0.552 C 87.363 51.239 86.039 52.48 84.455 52.48 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10;  opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" />
	<path d="M 60.328 63.309 c -0.637 0 -1.278 -0.201 -1.822 -0.618 L 41.932 49.995 c -0.741 -0.568 -1.176 -1.448 -1.176 -2.382 V 22.877 c 0 -1.657 1.343 -3 3 -3 s 3 1.343 3 3 v 23.255 l 15.397 11.795 c 1.316 1.008 1.565 2.891 0.558 4.206 C 62.121 62.905 61.229 63.309 60.328 63.309 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10;  fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" />
	<path d="M 49.373 17.185 c -0.56 0 -1.119 -0.156 -1.612 -0.47 c -1.023 -0.652 -1.553 -1.857 -1.342 -3.051 L 48.39 2.48 c 0.21 -1.195 1.12 -2.146 2.305 -2.408 c 1.19 -0.265 2.412 0.215 3.107 1.208 l 4.606 6.578 c 0.951 1.358 0.621 3.228 -0.736 4.178 l -6.578 4.606 C 50.578 17.003 49.975 17.185 49.373 17.185 z" style="stroke: none; stroke-width: 1; stroke-dasharray: none; stroke-linecap: butt; stroke-linejoin: miter; stroke-miterlimit: 10;  fill-rule: nonzero; opacity: 1;" transform=" matrix(1 0 0 1 0 0) " stroke-linecap="round" />
</g>
</svg>
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
    &-img{
      fill: $color500 !important;
    }
   
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
    &-flex{
      &-img{
        fill: $color100 !important;
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
      transform: translateX(30px);
    
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
