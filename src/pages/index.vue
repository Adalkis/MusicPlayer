<template>
  <div
    class="container"
    :style="{ backgroundColor: music[counter].backgroundColor }"
  >
    <div>
      <p>Playing {{ counter }} of 2</p>
      <img :src="music[counter].image" alt="" />
      <div>
        <p class="title">{{ music[counter].title }}</p>
        <p class="sub">{{ music[counter].sub }}</p>
      </div>
      <span>
        <button class="btn btn-primary btn-sm" @click="next">
          <i class="fas fa-step-backward"></i>
        </button>
      </span>

      <audio controls muted ref="audio" :src="music[counter].music"></audio>
      <span>
        <button class="btn btn-primary btn-sm" @click="next">
          <i class="fas fa-step-forward"></i>
        </button>
      </span>

      <div class="slidecontainer">
        <span>
          <i class="fas fa-volume-down"></i>
        </span>
        <input
          type="range"
          min="1"
          max="100"
          value="0"
          class="slider"
          id="myRange"
          @click="up"
          v-model="volume"
        />
        <span>
          <i class="fas fa-volume-up"></i>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
import music from "../music.json";
import image1 from "../assets/music.jpg";
import image2 from "../assets/piano.jpg";
import image3 from "../assets/guitar.jpg";

export default {
  name: "index",
  data() {
    return {
      music: [
        {
          music:
            "https://files.freemusicarchive.org/storage-freemusicarchive-org/music/WFMU/Broke_For_Free/Directionless_EP/Broke_For_Free_-_01_-_Night_Owl.mp3",
          image: image1,
          title: "Night Owl",
          sub: "Broke For Free",
          backgroundColor: "#ECCCB3",
        },
        {
          music:
            "https://files.freemusicarchive.org/storage-freemusicarchive-org/music/no_curator/Tours/Enthusiast/Tours_-_01_-_Enthusiast.mp3",
          image: image2,
          title: "Enthusiast",
          sub: "Tours",
          backgroundColor: "#EECFC6",
        },
        {
          music:
            "https://files.freemusicarchive.org/storage-freemusicarchive-org/music/ccCommunity/Chad_Crouch/Arps/Chad_Crouch_-_Shipping_Lanes.mp3",
          image: image3,
          title: "Shipping Lanes",
          sub: "Chad Crouch",
          backgroundColor: "#886C5A",
        },
      ],
      counter: 0,
      audio: music[0],
      volume: 0,
      found: 0,
    };
  },
  methods: {
    next() {
      this.counter = this.counter + 1;
      if (this.counter > 2) {
        this.counter = 0;
        console.log("estoy aqui");
      }
    },

    up() {
      var audio = this.$refs.audio;
      audio.volume = this.volume / 100;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img {
  width: 200px;
  height: 200px;
  border-radius: 30px;
}
button.btn.btn-primary.btn-sm {
  border: none;
  background: transparent;
  color: white;
  font-size: 22px;
  margin-top: 1-px;
  margin-top: -20px;
  padding: 10px;
}
audio {
  height: 20px;
}
i.fas.fa-volume-down {
  font-size: 10px;
}
i.fas.fa-volume-up {
  font-size: 10px;
}
html {
  background: #edf3f4;
}
.container {
  border-radius: 20px;
  width: 40%;
  margin-top: 70px;
}
p {
  font-family: "Font Awesome 5 Free";
  color: black;
}
p.title {
  font-size: 30px;
  font-family: cursive;
}
p.sub {
  margin-top: -20px;
}
input#myRange {
  height: 7px;

  background: black !important;
  margin: 10px 5px;
}
</style>
