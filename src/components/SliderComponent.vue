<template>
<div class="slide-area" :style="{backgroundColor: colorFromSliderValue}">
  <input type="range" v-model="sliderValue"> 
  <input type="text" v-model="sliderValue">
</div>
</template>

<script type="text/ecmascript-6">
export default {
    name: 'slider-component',
    data() {
        return {
            sliderValue: '10'
        }
    },
    computed: {
        colorFromSliderValue() {
            console.log('computed Called');
            if(this.sliderValue <= 10) {
                return 'red';
            } else if (this.sliderValue <= 40) {
                return 'orange';
            } else if (this.sliderValue <= 80) {
                return 'yellow';
            } else {
                return 'lightGreen';
            }
        }
    }

}
</script>

<style>
.slide-area {
    border: 1px solid black;
    border-radius: 3px;
    padding: 10px;
}
  
</style>
