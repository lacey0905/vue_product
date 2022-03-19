<template>
<div>
	<transition name="fade">
		<RoomModal @close="modalState = false" v-bind:rooms="rooms" v-bind:currentRooms="currentRooms" v-bind:modalState="modalState" />
	</transition>
	<Discount v-if="showDiscount" v-bind:discount="discount" />
	<div class="menu">
		<a v-for="(a,i) in menus" :key="i"> {{ a }} {{i}}</a>
	</div>

	<button @click="priceSort">낮은가격순정렬</button>
	<button @click="priceSortDown">높은가격순정렬</button>
	<button @click="nameSortDown">이름순정렬</button>
	<button @click="sortBack">되돌리기</button>

	<Card v-bind:rooms="rooms" @openModal="modalState = true; currentRooms=$event" />
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
			discount : 30,
			showDiscount : true,
			roomsOrigin : [...data],
			object : { name : 'kim', age : 20 },
			currentRooms : 0,
			rooms : data,
			modalState : false,
			menus : ['Home', 'Shop', 'About'],
			products : "a",
		}
	},
	mounted() {
		let timer = setInterval(() => {
			this.discount--;
			if(this.discount <= 0) {
				clearInterval(timer);
				this.showDiscount = false;
			}
			
		}, 1000);
	},
	
	components: {
		Discount,
		RoomModal,
		Card,
	},
	methods: {
		sortBack() {
			this.rooms = [...this.roomsOrigin];
		},
		priceSort() {
			this.rooms.sort((a,b) => {
				return a.price - b.price;
			});
		},
		priceSortDown() {
			this.rooms.sort((a,b) => {
				return b.price - a.price;
			});
		},
		nameSortDown() {
			this.rooms.sort((a,b) => {
				return a.title < b.title ? -1 : a.title > b.title ? 1 : 0;
			});
		},
	}
}
</script>

<style>
.fade-enter-from {
	transform: translateY(-100px);
	opacity: 0;
}
.fade-enter-active {
	transition: all 0.2s;
}
.fade-enter-to {
	opacity: 1;
	transform: translateY(0px);
}

.fade-leave-from {
	opacity: 1;
	transform: translateY(0px);
}
.fade-leave-active {
	transition: all 0.2s;
}
.fade-leave-to {
	opacity: 0;
	transform: translateY(-100px);
}

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
