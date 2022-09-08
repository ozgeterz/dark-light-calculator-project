<template>
  <div class="container">
    <div class="calculator">
      <div class="calculator-inner">
        <div class="calculator-inner-output">
          <h1>=</h1>
          <div class="calculator-inner-display">{{ display }}</div>
        </div>
        <div class="flex">
           <h1>Dark Mode toggle</h1>
        <div class="mode-toggle" @click="modeToggle" :class="darkDark">
            <div class="toggle">
                <div id="dark-mode" type="checkbox"></div>
            </div>
        </div>
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
            <div @click="append(1)" class="btn">1</div>
            <div @click="append(2)" class="btn">2</div>
            <div @click="append(3)" class="btn">3</div>
            <div @click="append(4)" class="btn">4</div>
            <div @click="append(5)" class="btn">5</div>
            <div @click="append(6)" class="btn">6</div>
            <div @click="append(7)" class="btn">7</div>
            <div @click="append(8)" class="btn">8</div>
            <div @click="append(9)" class="btn">9</div>
            <div @click="decimal" class="btn">.</div>
            <div @click="append(0)" class="btn">0</div>
            <div @click="append(0)" class="btn">00</div>
          </div>
        </div>
        <div class="calculator-under-right">
          <div class="calculator-under-right-operators">
            <div @click="divide" class="buton">÷</div>
            <div @click="multiply" class="buton">x</div>
            <div @click="subtract" class="buton">-</div>
            <div @click="add" class="buton">+</div>
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
            return this.darkMode && 'darkmode-toggled'
        }
    },


  data() { 
    return {
      previous: null,
      display: 0,
      operator: null,
      operatorClicked: false,
      darkMode: false,
    };
  },
  methods: {
    dark() {
            document.querySelector('body').classList.add('dark-mode')
            this.darkMode = true
            this.$emit('dark')
        },

        light() {
            document.querySelector('body').classList.remove('dark-mode')
            this.darkMode = false
            this.$emit('light')
        },

        modeToggle() {
            if(this.darkMode || document.querySelector('body').classList.contains('dark-mode')) {
                this.light()
            } else {
                this.dark()
            }
        },
/*
dark mod işlemleri bitti

*/

    clear() {
      this.display = 0;
    },
    sign() {
      this.display =
        this.display < 0
          ? (this.display = this.display - this.display * 2)
          : (this.display = this.display - this.display * 2);
    },
    percent() {
      this.display = this.display / 100;
    },
    append(number) {
      if (this.operatorClicked === true) {
        this.display = "";
        this.operatorClicked = false;
      }
      this.display =
        this.display === 0
          ? (this.display = number)
          : "" + this.display + number;
    },
    decimal() {
      if (this.display.indexOf(".") === -1) {
        this.append(".");
      }
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.previous = this.display;
      this.operatorClicked = true;
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.previous = this.display;
      this.operatorClicked = true;
    },
    subtract() {
      this.operator = (a, b) => a - b;
      this.previous = this.display;
      this.operatorClicked = true;
    },
    add() {
      this.operator = (a, b) => a + b;
      this.previous = this.display;
      this.operatorClicked = true;
    },
    equal() {
      this.display = this.operator(Number(this.previous), Number(this.display));
      this.previous = null;
      this.operatorClicked = true;
    },
  },
};
</script>
<style lang="scss" scoped>
.container {
  background: #e5e5e5;
  max-width: 100%;
  height: 100vh;
}
.calculator {
  position: relative;
  margin-inline-start: 35%;
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
    background: rgba(230, 246, 255, 0.2);
    box-shadow: 0px -5px 70px rgba(0, 0, 0, 0.1);
    border-radius: 30px;
    &-output {
      display: flex;
      gap: 270px;
      margin-top: 270px;
      margin-left: 50px;
    }
    &-display {
      font-size: 40px;
      line-height: 60px;
      overflow: visible;
      display: flex;
      align-items: center;
      text-align: right;
      color: #373737;
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
    background: linear-gradient(244.38deg, #60d8fd 10.14%, #98daf7 29.9%, #a4c9ff 70.94%);
    &-left {
      margin-inline-start: 7%;
      display: flex;
      flex-direction: column;
      margin-top: 30px;
      &-operations {
        display: flex;
        gap: 35px;
        width: 260px;
        height: 60px;
        background: rgba(255, 255, 255, 0.3);
        box-shadow: 0px 3px 15px rgba(0, 0, 0, 0.05);
        border-radius: 40px;
        &-operator {
          margin-left: 23px;
          font-size: 26px;
          cursor: pointer;
          display: flex;
          align-items: center;
        }
      }
      &-numbers {
        margin-top: 20px;
        display: grid;
        grid-template-columns: repeat(3, 1fr);

        gap: 25px;
        align-items: center;
        text-align: center;
      }
    }
    &-right {
      margin-top: 40px;
      align-items: center;
      text-align: center;
      width: 70px;
      height: 430px;
      background: rgba(255, 255, 255, 0.3);
      box-shadow: 0px 3px 15px rgba(0, 0, 0, 0.05);
      border-radius: 40px;
      &-operators {
        display: flex;
        flex-direction: column;
        margin-top: 25px;
        gap: 33px;
      }
    }
    &-bar {
      position: absolute;
      width: 175px;
      height: 5px;
      left: 124px;
      top: 483px;
      background: #6396c5;
      border-radius: 25px;
    }
  }
}
.btn {
  width: 70px;
  height: 70px;
  background: rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  font-family: "Poppins";
  font-style: normal;
  font-weight: 600;
  font-size: 26px;
  line-height: 66px;
  display: flex;
  display: block;
  margin: auto;
  color: #373737;
  cursor: pointer;
}
.buton {
  font-size: 26px;
  line-height: 50px;
  display: flex;
  display: block;
  margin: auto;
  color: #373737;
  cursor: pointer;
}

// _base.scss işlemleri başladııı


$dark: #2322;
$mode-toggle-bg: #262626;


body {
    background-color: #fff;
    color: $dark;
    transition: background-color .2s ease, color .2s ease;
}


// _dark-mode.scss
body {
    &.dark-mode {  
        .calculator{
         
          &-inner{
            background: linear-gradient(166.34deg, #373737 0%, #252628 22.9%, #000309 100%);         
              color:#FBFBFB;
            &-display{
              color:#FBFBFB;
            }
          }
          &-under{  
            background: linear-gradient(244.38deg, #42869B 8.14%, #2A7DA1 27.9%, #224E91 56.94%, #00123F 84.11%);
            color:#FBFBFB;
            &-left{
              &-operations{
                background: rgba(5, 5, 5, 0.3);

              }
              &-numbers{
              }
            }
            &-right{
              background: rgba(5, 5, 5, 0.3);
              &-operators{
                
              }
            }
          }
        }

        .btn{
          color: white;
          background: rgba(5, 5, 5, 0.3);
        }
        .buton{
          color:white;
          
        }
    }
}


// _mode-toggle.scss
.mode-toggle {
    position: relative;
    //margin: auto .5rem .5rem auto;
    padding: 0;
    width: 122px;
    height: 44px;
    background: #A9DCFD;
border-radius: 40px;
 
    border: 0;
 
    outline: 0;
    overflow: hidden;
    cursor: pointer;
    z-index: 2;
    -webkit-tap-highlight-color: rgba(0,0,0,0);
    -webkit-touch-callout: none;
    appearance: none;
    transition: background-color .5s ease;

    .toggle {
        position: absolute;
        top: 0;
        left: 0;
        bottom: 0;
        margin: auto;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        border: 3px solid transparent;
        box-shadow: inset 0 0 0 2px #a5abba;
        overflow: hidden;
        transition: transform .5s ease;
        #dark-mode {
            position: relative;
            width: 100%;
            height: 100%;
            overflow: hidden;
            border-radius: 50%;

            &:before {
                content: '';
                position: relative;
                width: 100%;
                height: 100%;
                left: 50%;
                float: left;
                background-color: #a6abba;
                transition: border-radius .5s ease, width .5s ease, height .5s ease, left .5s ease, transform .5s ease;
            }
        }
    }
}

body.dark-mode {
    .mode-toggle {
        background-color: lighten($mode-toggle-bg, 5%);

        .toggle {
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
.flex {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top:-300px;
    width: 100%;
    height: 100%;
}
</style>
