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

	<div>
		<img src="./assets/room0.jpg" class="room-img">
		<h4 v-on:click="modalState = true">{{products[0]}}</h4>
		<p>50만원</p>
		<button v-on:click="addCount(0)">허위매물신고</button>
		<span>신고수 : {{ reportCount[0] }}</span>
	</div>
	<div>
		<img src="./assets/room1.jpg" class="room-img">
		<h4>{{products[1]}}</h4>
		<p>50만원</p>
		<button v-on:click="addCount(1)">허위매물신고</button>
		<span>신고수 : {{ reportCount[1] }}</span>
	</div>
	<div>
		<img src="./assets/room2.jpg" class="room-img">
		<h4>{{products[2]}}</h4>
		<p>50만원</p>
		<button v-on:click="addCount(2)">허위매물신고</button>
		<span>신고수 : {{ reportCount[2] }}</span>
	</div>

</div>
</template>

<script>

export default {
	name: 'App',
	data(){
		return {
			modalState : false,
			reportCount : [0, 0, 0],
			menus : ['Home', 'Shop', 'About'],
			products : ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
		}
	},
	components: {

	},
	methods: {
		addCount(idx) {
			this.reportCount[idx]++;
		}
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
