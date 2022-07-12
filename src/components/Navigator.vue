<template>
  <div id="navigator">
    <button @click="restart()" id="reset">{{ this.messageRestart}}</button>
    <span id="message"> {{ this.message }} </span>

    <button id="easy" @click="easy()">easy</button>
    <button id="hard" @click="hard()" class="selected">hard</button>
    <Square :colorsNav="this.colors" :pickedColorNav="this.pickedColor" @messageSquare="message=$event" @messageRestart="messageRestart=$event"/>
  </div>
</template>

<script>
import Square from "./Square.vue";
export default {
  name: "src-components-navigator",
  props: [],
  components: {
    Square,
  },
  mounted() {
    this.colors = this.createNewColors(this.colorCount);
    this.pickedColor = this.colors[this.pickColor()];
    this.$emit('pickedColorNav',this.pickedColor)
  },
  data() {
    return {
      colorCount: 6,
      isHard: true,
      colors: [],
      pickedColor: '',
      message: '',
      messageRestart: 'New colors'
    };
  },
  methods: {
    easy(){
      if(this.isHard){
        console.log("Es easy!")
        this.isHard = false
        this.colorCount = 3
        this.restart()
      }
      
    },
    hard(){
      if(!this.isHard){
        this.isHard = true;
        this.colorCount = 6;
        this.restart()
      }
    },
    restart(){
      console.log("Restart!")
      this.colors = this.createNewColors(this.colorCount);
      this.pickedColor = this.colors[this.pickColor()];
      this.$emit('pickedColorNav',this.pickedColor)
      this.$emit('headerColor', 'steelblue')
      this.message = ''
      this.messageRestart = 'New Colors!'
    },
    pickColor() {
      var quantity;
      if (this.isHard) {
        quantity = 6;
      } else {
        quantity = 3;
      }
      return Math.floor(Math.random() * quantity);
    },
    createNewColors(numbers) {
      var arr = [];
      for (var i = 0; i < numbers; i++) {
        arr.push(this.createRandomStringColor());
      }
      return arr;
    },
    createRandomStringColor() {
      var newColor =
        "rgb(" +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ")";
      return newColor;
    },
    randomInt() {
      return Math.floor(Math.random() * 256);
    },
  },
  computed: {
      
  },
};
</script>

<style scoped lang="css">
#navigator {
  background: #ffffff;
  height: 30px;
  text-align: center;
  margin: 0;
  margin-top: -30px;
}
#message {
  color: #000000;
  display: inline-block;
  width: 20%;
}
.selected {
  background-color: steelblue;
  color: white;
}
button {
  border: none;
  background-color: white;
  font-family: "Montserrat", "Avenir";
  text-transform: uppercase;
  height: 100%;
  font-weight: 700;
  letter-spacing: 1px;
  color: steelblue;
  transition: all 0.3s;
  outline: none;
}
button:hover {
  color: white;
  background-color: steelblue;
}
</style>
