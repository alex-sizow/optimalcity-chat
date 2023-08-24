<script setup lang="ts">
const emits = defineEmits(['click']);

defineProps({
	value: { type: String },
});

const clickOnButton = () => {
	emits('click');
};
</script>

<template>
	<button
		class="button"
		@click="clickOnButton">
		{{ value }}
	</button>
</template>

<style scoped lang="scss">
.button {
	height: 44px;
	border-radius: 34px;
	background: linear-gradient(145deg, #ffc349, #dfa43d);
	box-shadow: 6px 6px 12px #dedede, -6px -6px 12px #ffffff;
	padding: 10px;
	color: white;
	display: flex;
	justify-content: center;
	align-items: center;
}
</style>
