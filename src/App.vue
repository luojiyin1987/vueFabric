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
  data(){
    return {
      width : window.innerWidth,
      height : window.innerHeight,
    }
  },
  methods: {
    
    initCanvas() {
      this.canvas = new fabric.Canvas('c');
      this.canvas.setWidth(this.width/2);
      this.canvas.setHeight(this.height/2);
      this.canvas.backgroundColor = '#fff';
      this.canvas.renderAll();
      console.log("this width",this.width);
    console.log("this height",this.height);
    },
  },
  mounted() {
      this.initCanvas();
    
    },
    

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
