<template>
<div>

	
	<RoomModal v-bind:rooms="rooms" v-bind:currentRooms="currentRooms" v-bind:modalState="modalState" />
	<Discount />

	<div class="menu">
		<a v-for="(a,i) in menus" :key="i"> {{ a }} {{i}}</a>
	</div>

	<Card v-bind:rooms="rooms" />

</div>
</template>

<script>

import RoomModal from './components/roomModal.vue';
import Discount from './components/discount.vue';
import Card from './components/Card.vue';
import data from './assets/data.js'

export default {
	name: 'App',
	data(){
		return {
			object : { name : 'kim', age : 20 },
			currentRooms : 0,
			rooms : data,
			modalState : false,
			menus : ['Home', 'Shop', 'About'],
			products : "a",
		}
	},
	components: {
		Discount,
		RoomModal,
		Card,
	},
	methods: {
	
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
}
.menu {
  background : darkslateblue;
  padding : 15px;
  border-radius : 5px;
}
.menu a {
  color : white;
  padding : 10px;
}
.room-img {
	width:100%;
	max-width:500px;
	margin-top:40px;
}
body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
} 

</style>
