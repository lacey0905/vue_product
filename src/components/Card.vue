<template>
    <div v-for="(item, i) in rooms" :key="i">
		<img :src="item.image" class="room-img">
		<!-- <h4 @click="modalState = true; currentRooms=i">{{ item.title }}</h4> -->
		<p>{{ item.content }}</p>
		<p>{{ item.price }}</p>
	</div>
</template>

<script>
export default {
    name : 'Card',
    props : {
        rooms : Array,
    }
}
</script>

<style>

</style>