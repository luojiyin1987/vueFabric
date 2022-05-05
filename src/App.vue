<template>
  <div id="app">
    <div class="center">
    
        <canvas id="c" ></canvas>
     </div>
  </div>
</template>

<script>
import { fabric } from "fabric";

export default {
  name: 'App',
  components: {
    
  },
  methods: {
    initCanvas() {
      this.canvas = new fabric.Canvas('label-canvas');
      this.canvas.setWidth(this.width/2);
      this.canvas.setHeight(this.height/2);
      this.canvas.backgroundColor = '#fff';
      this.canvas.renderAll();
    },
    addText() {
      this.canvas.add(new fabric.Text('Hello World', {
        left: 100,
        top: 100,
        fontSize: 40,
        fill: '#333'
      }));
      this.canvas.renderAll();
    },
    addImage() {
      fabric.Image.fromURL('./assets/logo.png', (img) => {
        img.set({
          left: 100,
          top: 100,
          angle: 0,
          padding: 10,
          cornersize: 10
        });
        img.scale(0.5);
        this.canvas.add(img);
        this.canvas.renderAll();
      });
    },
    addRect() {
      this.canvas.add(new fabric.Rect({
        left: 100,
        top: 100,
        fill: '#333',
        width: 100,
        height: 100
      }));
      this.canvas.renderAll();
    },
    addCircle() {
      this.canvas.add(new fabric.Circle({
        left: 100,
        top: 100,
        fill: '#333',
        radius: 50
      }));
      this.canvas.renderAll();
    },
  }
    

}
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
