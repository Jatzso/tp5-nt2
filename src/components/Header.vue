<template>

  <div id="header" :style="{backgroundColor: this.color}">
		<h1>The Great <br>
			<span id="colorDisplay">RGB {{ this.pickedColorNav }}</span>
			<br>
			Guessing Game</h1> 
      <Navigator @pickedColorNav="pickedColorNav=$event" @headerColor="color=$event"/>
	</div>
 

</template>

<script>
import Navigator from './Navigator.vue'
  export default  {
    name: 'src-components-header',
    props: [],
    components: {
      Navigator
    },
    mounted () {

    },
    data () {
      return {
        pickedColorNav: '',
        color: ''
      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  #header {
	transition: all 0.3s;
	background: steelblue;
	text-transform: uppercase;
	text-align: center;
	margin: 0;
	color: white;
	
}
#colorDisplay {
	font-size: 200%;
}
h1 {
	font-weight: normal;
	line-height: 1.1;
	padding: 20px 0;

}
</style>
