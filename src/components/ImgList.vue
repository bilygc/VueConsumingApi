<template>
    <div v-if="imgItem">			
			<img v-bind:src="imgItem.images.preview_gif.url">
    </div>
</template>

<script>
export default {
	name: 'ImgList'
}
</script>

<style>

</style>
