<template>
    <div class="black-bg" v-if="modalState">
		<div class="white-bg">
			<img :src="rooms[currentRooms].image" class="room-img">
			<h4>{{ rooms[currentRooms].title }}</h4>
			<p>{{ rooms[currentRooms].content}}</p>
			<input @input="month = $event.target.value" type="text" :value="month">
			<p>{{ month }}개월 선택함 : {{ rooms[currentRooms].price * month }}</p>
			<button @click="$emit('close')">닫기</button>
		</div>
	</div>
</template>

<script>
export default {
    name : 'roomModal',
	data(){
		return {
			month : 1,
		}
	},
	watch : {
		month(a,b) {
			if(a >= 13) {
				alert('13개월 이상 선택 할 수 없습니다.');
				this.month = b;
			} else if(isNaN(a)) {
				alert('숫자만 입력 하세요.')
				this.month = b;
			}
		},
	},
    props : {
        rooms : Array,
        currentRooms : Number,
        modalState : Boolean,
    }
}
</script>

<style>
	input {
		display: block;
		width:100px;
		height:30px;
		text-align: center;
		font-size:20px;
		margin:0 auto 20px;
	}
</style>