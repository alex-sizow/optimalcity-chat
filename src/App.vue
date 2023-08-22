<script setup lang="ts">
import Chat from './components/Chat.vue';
</script>

<template>
	<div class="container"><Chat msg="hi" /></div>
</template>

<style lang="scss" scoped>
.container {
	background: rgb(244, 235, 0);
	background: radial-gradient(
		circle,
		rgba(244, 235, 0, 1) 3%,
		rgba(222, 115, 159, 1) 50%,
		rgba(0, 231, 251, 1) 97%
	);
	width: 100%;
	height: 100vh;
	display: flex;
	justify-content: center;
	align-items: center;
}
</style>
