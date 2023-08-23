<script setup lang="ts">
import { ref } from 'vue';

import ChatInput from './ChatInput.vue';
import ChatMessage from './ChatMessage.vue';

const messages: any = ref([
	{
		type: 'robot',
		text: 'Привет, я утка, очень умная утка!',
		first: true,
	},
	{
		type: 'robot',
		text: 'Отвечай на мои вопросы чётко, лысая обезьяна!',
		first: false,
	},
]);

const inputField = ref('');

const pushMessage = () => {
	messages.value.push({
		type: 'you',
		text: inputField.value,
		first:
			messages.value.at(-1).type === 'you' ? false : true,
	});
	inputField.value = '';
};
</script>

<template>
	<div class="chat">
		<div class="chat__area">
			<chat-message
				v-for="(message, index) in messages"
				:key="index"
				:type="message.type"
				:text="message.text"
				:first="message.first" />
		</div>
		<div class="chat__input">
			<chat-input
				:value="inputField"
				v-model:value="inputField"
				@click="pushMessage" />
		</div>
	</div>
</template>

<style scoped lang="scss">
.chat {
	position: relative;
	width: 370px;
	height: 530px;
	background: white;
	box-shadow: 18px 18px 36px #d18c16, -18px -18px 36px #ffb61c;
	border-radius: 28px;
	display: flex;
	align-items: center;
	flex-direction: column;
	gap: 10px;
	padding-top: 12px;

	&__area {
		width: 99%;
		height: calc(100% - 25px);
		border-radius: 10px;
		overflow: auto;
		display: flex;
		flex-direction: column;
		gap: 10px;
		padding: 10px;

		.bot-message {
			display: flex;
			justify-content: right;
			flex-direction: column;
			.avatar {
				display: flex;
				align-items: center;
				column-gap: 12px;
				font-size: 18px;

				&__icon {
					width: 33px;
					height: 33px;
					padding: 2px 0 0 1.5px;
					border-radius: 50px;
					box-shadow: 3px 3px 6px #f2f2f2,
						-3px -3px 6px #ffffff;
					animation: fadeIn 0.5s;
				}
				&__description {
					animation: fadeIn 1s;
				}
			}
			.bot-message__items {
				display: flex;
				flex-direction: column;
				gap: 5px;
				animation: fadeIn 4s;
				margin: 10px 0 0 28px;
				div {
					font-family: monospace;
					font-weight: 600;
					font-size: 13px;
					line-height: 1.3;
					background: #3cd1e8;
					max-width: 170px;
					min-height: 40px;
					border-radius: 12px 25px 25px 12px;
					padding: 10px;
					box-shadow: 1px 1px 1px #6dcddc,
						-1px -1px 1px #79e3f4;
				}
				:first-child {
					border-radius: 0px 25px 25px 12px;
				}
			}
		}

		.answer-message {
			display: flex;
			flex-direction: column;
			width: 100%;
			.avatar {
				display: flex;
				justify-content: right;
				align-items: center;
				column-gap: 12px;
				font-size: 18px;

				&__icon {
					width: 33px;
					height: 33px;
					padding: 2px 0 0 1.5px;
					border-radius: 50px;
					box-shadow: 3px 3px 6px #f2f2f2,
						-3px -3px 6px #ffffff;
					animation: fadeIn 0.5s;
				}
				&__description {
					animation: fadeIn 1s;
				}
			}
			&__items {
				width: 100%;
				display: flex;
				align-items: end;
				flex-direction: column;
				gap: 5px;
				animation: fadeIn 4s;
				margin: 10px -25px;
				div {
					font-family: monospace;
					font-weight: 600;
					font-size: 13px;
					line-height: 1.3;
					background: #de7b98;
					max-width: 170px;
					min-height: 40px;
					border-radius: 25px 12px 12px 25px;
					padding: 10px;
					box-shadow: 1px 1px 1px #dd9db0,
						-1px -1px 1px #f5adc2;
				}
				:first-child {
					border-radius: 25px 0px 12px 25px;
				}
			}
		}
	}

	&__input {
		width: 100%;
		height: 65px;
		gap: 8px;
		padding: 0 10px;
		display: flex;
		justify-content: space-around;
		&_button {
			width: 44px;
			height: 44px;
			border-radius: 34px;
			background: linear-gradient(145deg, #ffc349, #dfa43d);
			box-shadow: 6px 6px 12px #dedede, -6px -6px 12px #ffffff;
			display: flex;
			justify-content: center;
			align-items: center;
		}
	}
}

@keyframes fadeIn {
	from {
		opacity: 0;
	}
	to {
		opacity: 1;
	}
}

@keyframes tt {
	from {
		background-size: 0 200%;
	}
}
@keyframes bb {
	50% {
		background-position: 0 -100%, 0 0;
	}
}
</style>
