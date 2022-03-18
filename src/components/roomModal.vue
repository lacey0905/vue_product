<template>
    <div class="black-bg" v-if="modalState">
		<div class="white-bg">
			<img :src="rooms[currentRooms].image" class="room-img">
			<h4>{{ rooms[currentRooms].title }}</h4>
			<p>{{ rooms[currentRooms].content}}</p>
			<p>{{ rooms[currentRooms].price}}</p>
			<!-- <button v-on:click="modalState = false">닫기</button> -->
		</div>
	</div>
</template>

<script>
export default {
    name : 'roomModal',
    props : {
        rooms : Array,
        currentRooms : Number,
        modalState : Boolean,
    }
}
</script>

<style>

</style>