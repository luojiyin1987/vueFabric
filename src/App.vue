<template>
  <div id="app">
    <div class="center">
      <canvas id="c"></canvas>
    </div>
    <div id="ctrlButton">
      <input id="fileUpload" type="file" hidden />
      <button id="addImage" @click="uploadImage()">Add Image</button>&nbsp;
      <button id="delImage" @click="delImage()">Delete Image</button>
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
      (this.canvas = new fabric.Canvas("c")),
        this.canvas.setWidth(this.width / 2);
      this.canvas.setHeight(this.height / 2);
      this.canvas.backgroundColor = "#fff";
      this.canvas.renderAll();
      console.log("this width", this.width);
      console.log("this height", this.height);
    },

    uploadImage() {
      document.getElementById("fileUpload").click();
      //mounted run initUpload  function
    },

    delImage() {
      this.canvas.remove(this.canvas.getActiveObject());
      //this.canvas.renderAll();
    },

    initUpload() {
      const tempCanvas = this.canvas;
      document
        .getElementById("fileUpload")
        .addEventListener("change", function (e) {
          const file = e.target.files[0];

          const reader = new FileReader();
          reader.onload = function (f) {
            const data = f.target.result;

            fabric.Image.fromURL(data, function (img) {
              const scale = tempCanvas.width / img.width / 2;
              var oImg = img.set({ angle: 0 }).scale(scale);
              tempCanvas.add(oImg).renderAll();
              tempCanvas.canvas.setActiveObject(oImg);
            });
          };
          reader.readAsDataURL(file);
        });
    },
  },
  mounted() {
    this.initCanvas();
    this.initUpload();
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
