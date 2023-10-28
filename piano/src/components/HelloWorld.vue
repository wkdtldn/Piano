<template>
  <div id="app">
    <div class="center_box">
      <h2>Vue.js Piano</h2>
      <button @click="Play()" class="pe-3">Play/Stop</button>
      <button @click="Reset()">Reset</button>
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
        // 1 line
        { key: 10, interval: 2000 },
        { key: 9, interval: 2000 },
        { key: 8, interval: 2000 },
        { key: 7, interval: 2000 },
        { key: 6, interval: 2000 },
        { key: 5, interval: 2000 },
        { key: 6, interval: 2000 },
        { key: 7, interval: 2000 },
        // 도돌임표
        { key: 10, interval: 2000 },
        { key: 9, interval: 2000 },
        { key: 8, interval: 2000 },
        { key: 7, interval: 2000 },
        { key: 6, interval: 2000 },
        { key: 5, interval: 2000 },
        { key: 6, interval: 2000 },
        { key: 7, interval: 2000 },
        // 2 line
        { key: 10, interval: 1000 },
        { key: 8, interval: 500 },
        { key: 9, interval: 500 },
        { key: 10, interval: 1000 },
        { key: 9, interval: 500 },
        { key: 8, interval: 500 },
        { key: 9, interval: 500 },
        { key: 7, interval: 500 },
        { key: 8, interval: 500 },
        { key: 9, interval: 500 },
        { key: 10, interval: 500 },
        { key: 9, interval: 500 },
        { key: 8, interval: 500 },
        { key: 7, interval: 500 },
        { key: 8, interval: 1000 },
        { key: 6, interval: 500 },
        { key: 7, interval: 500 },
        { key: 8, interval: 1000 },
        { key: 3, interval: 500 },
        { key: 4, interval: 500 },
        { key: 5, interval: 500 },
        { key: 6, interval: 500 },
        { key: 5, interval: 500 },
        { key: 4, interval: 500 },
        { key: 5, interval: 500 },
        { key: 8, interval: 500 },
        { key: 7, interval: 500 },
        { key: 8, interval: 500 },
        // 3 line
        { key: 6, interval: 1000 },
        { key: 8, interval: 500 },
        { key: 7, interval: 500 },
        { key: 6, interval: 1000 },
        { key: 5, interval: 500 },
        { key: 4, interval: 500 },
        { key: 5, interval: 500 },
        { key: 4, interval: 500 },
        { key: 3, interval: 500 },
        { key: 4, interval: 500 },
        { key: 5, interval: 500 },
        { key: 6, interval: 500 },
        { key: 7, interval: 500 },
        { key: 8, interval: 500 },
        { key: 6, interval: 1000 },
        { key: 8, interval: 500 },
        { key: 7, interval: 500 },
        { key: 8, interval: 1000 },
        { key: 7, interval: 500 },
        { key: 8, interval: 500 },
        { key: 7, interval: 500 },
        { key: 5, interval: 500 },
        { key: 6, interval: 500 },
        { key: 7, interval: 500 },
        { key: 8, interval: 500 },
        { key: 9, interval: 500 },
        { key: 10, interval: 500 },
        { key: 11, interval: 500 },
        // 4 line
        { key: 12, interval: 1000 },
        { key: 10, interval: 500 },
        { key: 11, interval: 500 },
        { key: 12, interval: 1000 },
        { key: 10, interval: 500 },
        { key: 11, interval: 500 },
        { key: 12, interval: 500 },
        { key: 5, interval: 500 },
        { key: 6, interval: 500 },
        { key: 7, interval: 500 },
        { key: 8, interval: 500 },
        { key: 9, interval: 500 },
        { key: 10, interval: 500 },
        { key: 11, interval: 500 },
        { key: 10, interval: 1000 },
        { key: 8, interval: 500 },
        { key: 9, interval: 500 },
        { key: 10, interval: 1000 },
        { key: 3, interval: 500 },
        { key: 4, interval: 500 },
        { key: 5, interval: 500 },
        { key: 6, interval: 500 },
        { key: 5, interval: 500 },
        { key: 4, interval: 500 },
        { key: 5, interval: 500 },
        { key: 8, interval: 500 },
        { key: 7, interval: 500 },
        { key: 8, interval: 500 },
        // 도돌임표
        { key: 12, interval: 1000 },
        { key: 10, interval: 500 },
        { key: 11, interval: 500 },
        { key: 12, interval: 1000 },
        { key: 10, interval: 500 },
        { key: 11, interval: 500 },
        { key: 12, interval: 500 },
        { key: 5, interval: 500 },
        { key: 6, interval: 500 },
        { key: 7, interval: 500 },
        { key: 8, interval: 500 },
        { key: 9, interval: 500 },
        { key: 10, interval: 500 },
        { key: 11, interval: 500 },
        { key: 10, interval: 1000 },
        { key: 8, interval: 500 },
        { key: 9, interval: 500 },
        { key: 10, interval: 1000 },
        { key: 3, interval: 500 },
        { key: 4, interval: 500 },
        { key: 5, interval: 500 },
        { key: 6, interval: 500 },
        { key: 5, interval: 500 },
        { key: 4, interval: 500 },
        { key: 5, interval: 500 },
        { key: 8, interval: 500 },
        { key: 7, interval: 500 },
        { key: 8, interval: 500 },
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
      audioPlay: { status: "STOP", position: 0 },
    };
  },
  methods: {
    async Play() {
      const wait = (timeToDelay) =>
        new Promise((resolve) => setTimeout(resolve, timeToDelay));
      this.audioPlay.status =
        this.audioPlay.status == "START" ? "STOP" : "START";
      while (this.audioPlay.position < this.autoKeys.length) {
        console.log(this.audioPlay.position);
        if (this.audioPlay.status != "START") {
          break;
        } else {
          if (this.audioPlay.position >= this.autoKeys.length) {
            this.audioPlay.status = "STOP";
            break;
          } else {
            await this.play(this.autoKeys[this.audioPlay.position].key);
            await wait(this.autoKeys[this.audioPlay.position].interval);
            this.audioPlay.position++;
          }
        }
      }
    },
    async Reset() {
      this.audioPlay.status = "RESET";
      this.audioPlay.position = 0;
    },
    animation(code) {
      this.pianoKeys.forEach((item) => {
        if (code === item.code) {
          this.keyPress(item.keyboard);
          setTimeout(() => {
            this.keyNotPress(item.keyboard);
          }, this.autoKeys[this.index].interval);
        }
      });
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
          console.log(item.name);
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
