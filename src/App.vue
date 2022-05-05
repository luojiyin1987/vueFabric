<template>
  <div id="app">
    <div class="center">
      <canvas id="c"></canvas>
    </div>
    <div id="ctrlButton">
      <input id="fileUpload" type="file" hidden />
      <button id="addImage" @click="uploadImage()">Add Image</button>&nbsp;
      <button id="delImage">Delete Image</button>
    </div>
  </div>
</template>

<script>
import { fabric } from "fabric";

export default {
  name: "App",
  components: {},
  data() {
    return {
      width: window.innerWidth,
      height: window.innerHeight,
      canvas: null,
    };
  },
  methods: {
    initCanvas() {
      this.canvas = new fabric.Canvas("c");
      this.canvas.setWidth(this.width / 2);
      this.canvas.setHeight(this.height / 2);
      this.canvas.backgroundColor = "#fff";
      this.canvas.renderAll();
      console.log("this width", this.width);
      console.log("this height", this.height);
    },

    uploadImage() {
      document.getElementById("fileUpload").click();
      const file = document.getElementById("fileUpload").files[0];

      var pugImg = new Image();
      pugImg.onload = function () {
        var pug = new fabric.Image(pugImg, {
          angle: 45,
          width: 500,
          height: 500,
          left: 50,
          top: 70,
          scaleX: 0.25,
          scaleY: 0.25,
        });
        this.canvas.add(pug);
      };

      pugImg.src = URL.createObjectURL(file);
    },
  },
  mounted() {
    this.initCanvas();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}
</style>
