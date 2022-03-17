<template>
<div>

	<div class="black-bg" v-if="modalState">
		<div class="white-bg">
			<h4>상세페이지</h4>
			<p>상세페이지내용임</p>
			<button v-on:click="modalState = false">닫기</button>
		</div>
	</div>

	<div class="menu">
		<a v-for="(a,i) in menus" :key="i"> {{ a }} {{i}}</a>
	</div>

	<div v-for="(item, i) in rooms" :key="i">
		<img :src="item.image" class="room-img">
		<h4>{{ item.title }}</h4>
		<p>{{ item.content }}</p>
		<p>{{ item.price }}</p>
	</div>

</div>
</template>

<script>

import data from './assets/data.js'

export default {
	name: 'App',
	data(){
		return {
			rooms : data,
			modalState : false,
			menus : ['Home', 'Shop', 'About'],
			products : "a",
		}
	},
	components: {

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
