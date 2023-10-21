<template>
  <div id="app">
    <div class="center_box">
      <h2>Vue.js Piano</h2>
      <button @click="start()" v-if="test == true">start</button>
      <button @click="stop()">stop</button>
      <div style="height: 20px"></div>
      <div class="keyboard">
        <div class="pianokey" v-for="(item, index) in pianoKeys">
          <span
            v-if="item.type == 'white'"
            class="white"
            type="button"
            :index="index"
            @click="play(item.code)"
          ></span>
          <span
            v-if="item.type == 'black'"
            class="black"
            type="button"
            @click="play(item.code)"
          ></span>
          <div class="pianotext">
            {{ item.name }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  created() {
    window.onkeydown = (q) => {
      this.keyPress(q.key);
      this.kbPlay(q.key);
    };
    window.onkeyup = (q) => {
      this.keyNotPress(q.key);
    };
  },
  data() {
    return {
      autoKeys: [
        3, 2, 1, 2, 3, 3, 3, 2, 2, 2, 3, 3, 3, 3, 2, 1, 2, 3, 3, 3, 2, 2, 3, 2,
        1,
      ],
      pianoKeys: [
        { code: 1, type: "white", keyboard: "q", name: "도" },
        { code: 1.5, type: "black", keyboard: "2", name: "도#" },
        { code: 2, type: "white", keyboard: "w", name: "레" },
        { code: 2.5, type: "black", keyboard: "3", name: "레#" },
        { code: 3, type: "white", keyboard: "e", name: "미" },
        { code: 4, type: "white", keyboard: "r", name: "파" },
        { code: 4.5, type: "black", keyboard: "5", name: "파#" },
        { code: 5, type: "white", keyboard: "t", name: "솔" },
        { code: 5.5, type: "black", keyboard: "6", name: "솔#" },
        { code: 6, type: "white", keyboard: "y", name: "라" },
        { code: 6.5, type: "black", keyboard: "7", name: "라#" },
        { code: 7, type: "white", keyboard: "u", name: "시" },
        { code: 8, type: "white", keyboard: "z", name: "도" },
        { code: 8.5, type: "black", keyboard: "s", name: "도#" },
        { code: 9, type: "white", keyboard: "x", name: "레" },
        { code: 9.5, type: "black", keyboard: "d", name: "레#" },
        { code: 10, type: "white", keyboard: "c", name: "미" },
        { code: 11, type: "white", keyboard: "v", name: "파" },
        { code: 11.5, type: "black", keyboard: "g", name: "파#" },
        { code: 12, type: "white", keyboard: "b", name: "솔" },
        { code: 12.5, type: "black", keyboard: "h", name: "솔#" },
        { code: 13, type: "white", keyboard: "n", name: "라" },
        { code: 13.5, type: "black", keyboard: "j", name: "라#" },
        { code: 14, type: "white", keyboard: "m", name: "시" },
        { code: 15, type: "white", keyboard: ",", name: "도" },
      ],
      index: 0,
      test: true,
      test_func: null,
    };
  },
  methods: {
    start() {
      console.log("start!");
      this.test = true;
      this.test_func = setInterval(() => {
        this.log(true);
      }, 500);
    },
    stop() {
      console.log("stop!!");
      this.test = false;
      clearInterval(this.test_func);
    },
    log(x) {
      console.log("pop!");
    },
    keyPress(key) {
      const test = document.querySelectorAll("span");
      this.pianoKeys.forEach((item, index) => {
        if (item.keyboard === key) {
          if (item.type === "white") test[index].classList.add("active_white");
          else test[index].classList.add("active_black");
        }
      });
    },
    keyNotPress(key) {
      const test = document.querySelectorAll("span");
      this.pianoKeys.forEach((item, index) => {
        if (item.keyboard === key) {
          if (item.type === "white")
            test[index].classList.remove("active_white");
          else test[index].classList.remove("active_black");
        }
      });
    },
    play(code) {
      var audio = new Audio(
        "https://awiclass.monoame.com/pianosound/set/" + code + ".wav"
      );
      audio.play();
    },
    kbPlay(key) {
      let keyIndex;
      this.pianoKeys.every((item) => {
        if (item.keyboard === key) {
          keyIndex = item.code;
          var audio = new Audio(
            "https://awiclass.monoame.com/pianosound/set/" + keyIndex + ".wav"
          );
          audio.play();
          return false;
        } else {
          return true;
        }
      });
    },
  },
};
</script>
<style>
* {
  backface-visibility: hidden;
}

html,
body {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
}

h2 {
  margin-bottom: 30px;
}

.center_box {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  width: 100%;
}

.keyboard {
  box-shadow: 0px 0px 40px -5px rgba(0, 0, 0, 0.4);
  display: inline-block;
  cursor: pointer;
  margin-bottom: 30px;
}

.pianokey {
  display: inline-block;
  vertical-align: top;
  position: relative;
}

.white {
  position: absolute;
  width: 44px;
  height: 300px;
  border: solid 1px #eee;
  display: inline-block;
  position: relative;
  background-color: #fff;
  border: solid 1px rgba(0, 0, 0, 0.1);
  left: 0px;
  top: 0px;
  z-index: 0;
  transform: translate(-3px, -3px);
  transition: 0.1s;
}
.white:active {
  transform: translate(0px, 0px);
  background-color: #eee;
}

.black {
  position: relative;
  width: 22px;
  height: 165px;
  margin-left: -11px;
  margin-right: -11px;
  background-color: #585858;
  z-index: 20;
  transform: translate(-3px, -3px);
  transition: 0.1s;
}
.black:active {
  transform: translate(0px, 0px);
  background-color: #3f3f3f;
}
.pianotext {
  width: 99%;
  position: absolute;
  bottom: 15px;
  pointer-events: none;
}
.active_black {
  transform: translate(0px, 0px);
  background-color: #3f3f3f;
}
.active_white {
  transform: translate(0px, 0px);
  background-color: #eee;
}
</style>
