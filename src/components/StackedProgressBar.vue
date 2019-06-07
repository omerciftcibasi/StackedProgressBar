<template>
<div>
    <div>

<div v-if="labelLocation==='outside'" style="float:left;    min-width: 100%; text-align:center;    display: -webkit-box;">
      <div class="barItem" v-for="(item,index) in list" :style="' width:' + item.percentage +'%;'" :key="index">
        <div style="width:100%;  color: #222;">
      <span style="font-size: 14px; font-weight:bold;">{{item.text}}</span><br>
      <span style="font-size: 12px;">{{item.description}}</span><br>
      <div class="line">

      </div>
<div class="circle">

      </div>

        </div>
      </div>
    </div>
    
</div>
  <div class="main">
    
    <div class="barItem" v-for="(item,index) in list" :style="itemColor(item,index) + ' width:' + item.percentage +'%;'" :key="index">
    <span v-if="labelLocation==='inside'" class="insideLabel">{{item.text}}</span>
    </div>
  </div>
</div>
</template>
<script>
import { toColorObject } from "../assets/w3color.js";
export default {
  name: 'StackedProgressBar',
  props: {
    list: {
      type: Array,
      default: null
    },
    striped: {
      type: Boolean,
      default: false
    },
    labelLocation: {
      type: String,
      default: 'inside'
    }
  },
  methods: {
    itemColor(item,index) {
      if (item.color) {
        // eslint-disable-next-line no-console
        var color = toColorObject(item.color)
        var h = color.hue
        var s = color.sat*100
        var l = color.lightness*100
        var ll = l>50? l-25: l+25 
        var ss = s>50? s-15: s+15 



        
        // eslint-disable-next-line no-console
      //  console.log(c)
      //return 'background-color: rgba(red('+item.color+'), green('+item.color+'), blue('+item.color+'), 0.2);'
      if (item.striped) {
        return `background: repeating-linear-gradient(135deg, hsl(${h}, ${s}%, ${l}%), hsl(${h}, ${s}%, ${l}%) 10px, hsl(${h}, ${ss}%, ${ll}%) 10px, hsl(${h}, ${ss}%, ${ll}%) 15px);`
      }else{
        return `background-color:hsl(${h}, ${s}%, ${l}%);`
      }
      } else {
        if (item.striped) {
        return `background: repeating-linear-gradient(45deg, hsl(calc(360/${index+1}),50%,25%), hsl(calc(360/${index+1}),75%,25%) 10px,hsl(calc(360/${index+1}),50%,75%) 10px,hsl(calc(360/${index+1}),75%,75%) 20px);`
          
        } else {
          return `background-color:hsl(calc(360/${index+1}),50%,25%);`
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main {
  height: 20px;
    min-width: 100%;
    border-radius: 8px;
    background-color: #FAFAFA;
    display: -webkit-box;
    overflow: hidden;
    float: left;
    border: solid 1px #E0E0E0;
    /* -webkit-box-shadow: inset -2px 3px 6px 1px rgba(0,0,0,0.42); */
    -moz-box-shadow: inset -2px 3px 6px 1px rgba(0,0,0,0.42);
    box-shadow: inset -1px 1px 2px 1px #E0E0E0;
}
.barItem {
  font-size:12px; 
  color:white; 
  text-align:center;
  vertical-align: middle;
}

.insideLabel {
  background-color: #0000007d;
    padding: 3px;
    vertical-align: middle;
    font-weight: bolder;
}

.outsiteLabel {
    position: relative;
    top: 200px;
    left: 200px;
    color: crimson;
    z-index: 90;
    display: block;
}

.line {
  width: 4px;
    background-color: lightslategray;
    height: 40px;
    border-radius: 3px 3px 0px 0px;
    margin-left: calc(50% - 2px);
}

.circle {
  width: 10px;
    height: 10px;
    border-radius: 50%;
    margin-left: calc(50% - 5px);
    background-color: lightslategray;

}
</style>
