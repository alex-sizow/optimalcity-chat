<script setup lang="ts">
const emits = defineEmits(['update:value', 'click']);
defineProps({
	text: { type: String },
});

const updateValue = (event: any) => {
	emits('update:value', event.target.value);
};

const clickOnButton = () => {
	emits('click');
};
</script>

<template>
	<input
		placeholder="Введите текст"
		type="text"
		class="input"
		:value="text"
		@input="updateValue($event)" />
	<button
		class="button"
		@click="clickOnButton">
		<svg
			width="33"
			height="33"
			fill="#ffffff"
			viewBox="0 0 24 24"
			xmlns="http://www.w3.org/2000/svg">
			<path
				fill-rule="evenodd"
				d="M21.6 12c0 4.64-4.298 8.4-9.6 8.4a10.609 10.609 0 0 1-4.9-1.176L2.4 20.4l1.606-3.748C2.992 15.32 2.4 13.721 2.4 12c0-4.64 4.298-8.4 9.6-8.4s9.6 3.76 9.6 8.4ZM8.4 10.8H6v2.4h2.4v-2.4Zm9.6 0h-2.4v2.4H18v-2.4Zm-7.2 0h2.4v2.4h-2.4v-2.4Z"
				clip-rule="evenodd"></path>
		</svg>
	</button>
</template>

<style scoped>
.input {
	width: calc(100% - 55px);
	height: 45px;
	background-color: white;
	border-radius: 28px;
	padding: 0 20px;
	box-shadow: inset 4px 4px 8px #ebb455,
		inset -4px -4px 9px #ffce4d;
}
.button {
	width: 44px;
	height: 44px;
	border-radius: 34px;
	background: linear-gradient(145deg, #ffc349, #dfa43d);
	box-shadow: 6px 6px 12px #dedede, -6px -6px 12px #ffffff;
	display: flex;
	justify-content: center;
	align-items: center;
}
</style>
