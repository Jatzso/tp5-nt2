<template>
  <div id="container">
    <div
      class="square"
      v-for="(color, index) in this.colorsNav"
      :key="index"
      :style="{ backgroundColor: color }"
      @click="click(color)"
    ></div>
  </div>
</template>

<script>
export default {
  name: "src-components-square",
  props: ["colorsNav", "pickedColorNav"],
  mounted() {},
  data() {
    return {
      messageWin: 'You Picked Right!',
      messageRestart: 'Play Again!',
      messageTryAgain: 'Try Again!'
    };
  },
  methods: {
    setAllColorsTo(color){
      var squares = document.querySelectorAll(".square");
        squares.forEach(function(square) {
          square.style.backgroundColor = color
        })
    },
    click(color){
      if(color == this.pickedColorNav){
        this.$emit('messageSquare', this.messageWin)
        this.setAllColorsTo(color)
        this.$emit('messageRestart', this.messageRestart)
      }else{
        this.$emit('messageSquare', this.messageTryAgain)
        

      }
    }
  },
  computed: {},
};
</script>

<style scoped lang="css">
.square {
  width: 30%;
  background: blue;
  padding-bottom: 30%;
  float: left;
  margin: 1.66%;
  border-radius: 10%;
  transition: background 0.8s;
  -webkit-transition: background 0.8s;
  -moz-transition: background 0.8s;
}
#container {
  margin: 20px auto;
  max-width: 600px;
}
</style>
