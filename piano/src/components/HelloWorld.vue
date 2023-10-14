<template>
  <div id="piano">
    <div id="piano-container">
      <li>
        <button class="white" @click="play(1)">도</button
        ><button class="black" @click="play(1.5)">도#</button>
      </li>
    </div>
  </div>
  <v-btn class="white" @click="play(1)">도</v-btn>
  <v-btn class="black" @click="play(1.5)">도#</v-btn>
  <v-btn @click="play(2)">레</v-btn>
  <v-btn @click="play(2.5)">레#</v-btn>
  <v-btn @click="play(3)">미</v-btn>
  <v-btn @click="play(4)">파</v-btn>
  <v-btn @click="play(4.5)">파#</v-btn>
  <v-btn @click="play(5)">솔</v-btn>
  <v-btn @click="play(5.5)">솔#</v-btn>
  <v-btn @click="play(6)">라</v-btn>
  <v-btn @click="play(6.5)">라#</v-btn>
</template>
<!-- [1, 1.5, 2, 2.5,3,4,4.5,5,5.5,6,6.5,7,8,8.5,9,9.5,10,11,11.5,12,12.5,13,13.5,14,15] -->
<script>
export default {
  methods: {
    play(index) {
      var audio = new Audio(
        "https://awiclass.monoame.com/pianosound/set/" + index + ".wav"
      );
      audio.play();
    },
  },
};
</script>
<style>
body {
  background: mistyrose;
  font-family: "Great Vibes", cursive;
}
#piano {
  margin-top: 10% !important;
}
#piano {
  margin-top: 10%;
  width: 600px;
  height: 300px;
  margin: auto;
  border-radius: 20px 20px 0 0;
  overflow: hidden;
  background: -webkit-linear-gradient(#111, #444);
  background: -o-linear-gradient(#222, #444);
  background: -moz-linear-gradient(#222, #444);
  background: linear-gradient(#1e1d1d, #000);
}
.light {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: #ff7700;
  float: left;
  margin-right: 10px;
  margin-top: 25px;
}
.text {
  float: left;
  width: 10%;
}
.text h1 {
  font-family: metropolis;
  font-size: 38px;
  color: #eee;
  line-height: 60px;
}
#piano-container {
  width: 95%;
  height: 230px;
  background: #fff;
  margin: 60px auto 0 auto;
}
#piano-container li {
  width: 14.28%;
  height: 100%;
  float: left;
  list-style-type: none;
  position: relative;
}
.white {
  width: 100%;
  height: 100%;
  float: left;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.5);
  position: relative;
  z-index: 1;
  background: #f5f5f5;
}
button:focus {
  outline: none;
}
.white:active {
  box-shadow: -1px 0 15px rgba(0, 0, 0, 0.7) inset;
  -webkit-box-shadow: -1px 0 15px rgba(0, 0, 0, 0.7) inset;
  -moz-box-shadow: -1px 0 15px rgba(0, 0, 0, 0.7) inset;
  -ms-box-shadow: -1px 0 15px rgba(0, 0, 0, 0.7) inset;
}
.white:active #goat {
  background-image: url(../img/Goat.gif);
}
.black {
  position: absolute;
  border: none;
  z-index: 2;
  width: 70%;
  height: 120px;
  background: #000;
  right: -35%;
  box-shadow: 1px 0 #111, 0 2px 0 #111, 0 3px 0 #333, 0 4px 0 #333, 0 5px 0 #333,
    0 6px 1px rgba(0, 0, 0, 0.1), 0 0 5px rgba(0, 0, 0, 0.1),
    0 1px 3px rgba(0, 0, 0, 0.3), 0 3px 5px rgba(0, 0, 0, 0.2),
    0 5px 10px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.2),
    0 20px 20px rgba(0, 0, 0, 0.15);
  -webkit-box-shadow: 1px 0 #777, 0 2px 0 #777, 0 3px 0 #666, 0 4px 0 #555,
    0 5px 0 #444, 0 6px 1px rgba(0, 0, 0, 0.1), 0 0 5px rgba(0, 0, 0, 0.1),
    0 1px 3px rgba(0, 0, 0, 0.3), 0 3px 5px rgba(0, 0, 0, 0.2),
    0 5px 10px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.2),
    0 20px 20px rgba(0, 0, 0, 0.15);
  -moz-box-shadow: 1px 0 #333, 0 2px 0 #555, 0 3px 0 #555, 0 4px 0 #666,
    0 5px 0 #777, 0 6px 1px rgba(0, 0, 0, 0.1), 0 0 5px rgba(0, 0, 0, 0.1),
    0 1px 3px rgba(0, 0, 0, 0.3), 0 3px 5px rgba(0, 0, 0, 0.2),
    0 5px 10px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.2),
    0 20px 20px rgba(0, 0, 0, 0.15);
  -ms-box-shadow: 1px 0 #333, 0 2px 0 #555, 0 3px 0 #555, 0 4px 0 #666,
    0 5px 0 #777, 0 6px 1px rgba(0, 0, 0, 0.1), 0 0 5px rgba(0, 0, 0, 0.1),
    0 1px 3px rgba(0, 0, 0, 0.3), 0 3px 5px rgba(0, 0, 0, 0.2),
    0 5px 10px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.2),
    0 20px 20px rgba(0, 0, 0, 0.15);
}
.black:active {
  box-shadow: 1px 0 #777, 0 2px 0 #777, 0 3px 0 #666, 0 4px 0 #555;
  -webkit-box-shadow: 1px 0 #555, 0 1px 0 #555, 0 1px 0 #444, 0 2px 0 #333;
  -moz-box-shadow: 1px 0 #111, 0 2px 0 #222, 0 3px 0 #222;
  -ms-box-shadow: 1px 0 #111, 0 2px 0 #222, 0 3px 0 #222;
}
</style>
