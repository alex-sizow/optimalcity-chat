<script setup lang="ts">
import type { Ref } from 'vue';
import { ref } from 'vue';

import ChatButton from './ChatButton.vue';
import ChatInput from './ChatInput.vue';
import ChatMessage from './ChatMessage.vue';

const messages: Ref = ref([
	{
		type: 'robot',
		text: 'Привет, я утка, очень умная утка!',
		first: true,
	},
	{
		type: 'robot',
		text: 'Как тебе помочь?',
		first: false,
	},
]);

const inputField = ref('');
const buttons = ref(false);

setTimeout(() => {
	buttons.value = true;
}, 1800);

const answerMessage = (text: string) => {
	const currentDate = new Date();

	const hours = currentDate.getHours();
	const minutes = currentDate.getMinutes();

	setTimeout(() => {
		if (/[a-zA-Z]/.test(text)) {
			messages.value.push({
				type: 'robot',
				text: 'Пиши на русском( Я потом выучу английский!',
				first: true,
			});
		} else if (text === 'Сколько время?') {
			messages.value.push({
				type: 'robot',
				text: `Сейчас: ${hours}:${minutes}`,
				first: true,
			});
		} else if (text.includes('кря')) {
			messages.value.push({
				type: 'robot',
				text: `Кря! Кря! Кря!`,
				first: true,
			});
		} else if (messages.value.length > 4) {
			messages.value.push({
				type: 'robot',
				text: 'Я устала( Ты скучный!',
				first: true,
			});
		} else {
			messages.value.push({
				type: 'robot',
				text: 'Мне это не интересно. Тебе нравятся круассаны?',
				first: true,
			});
		}
	}, 1500);
	setTimeout(() => {
		buttons.value = true;
	}, 1800);
};

const pushMessage = (input: string) => {
	buttons.value = false;
	messages.value.push({
		type: 'you',
		text: input,
		first:
			messages.value.at(-1).type === 'you' ? false : true,
	});
	answerMessage(input);
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
				:first="message.first"
				:ref="`${index}`" />
		</div>
		<div
			v-if="buttons"
			class="chat__buttons">
			<chat-button
				value="Скажи кря!"
				@click="pushMessage('Скажи кря!')" />
			<chat-button
				value="Сколько время?"
				@click="pushMessage('Сколько время?')" />
		</div>
		<div class="chat__input">
			<chat-input
				:text="inputField"
				v-model:value="inputField"
				@click="pushMessage(inputField)" />
		</div>
	</div>
</template>

<style scoped lang="scss">
.chat {
	position: relative;
	width: 380px;
	height: 600px;
	background: white;
	box-shadow: 18px 18px 36px #d18c16, -18px -18px 36px #ffb61c;
	border-radius: 28px;
	display: flex;
	align-items: center;
	flex-direction: column;
	gap: 10px;
	padding-top: 20px;

	&__area {
		width: 99%;
		height: calc(100% - 45px);
		border-radius: 10px;
		overflow: auto;
		display: flex;
		flex-direction: column;
		gap: 10px;
		padding: 10px;
		scrollbar-gutter: stable;
		overscroll-behavior-y: none;
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

		::-webkit-scrollbar {
			width: 10px;
		}

		::-webkit-scrollbar-track {
			background-color: darkgrey;
		}

		::-webkit-scrollbar-thumb {
			box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
		}
	}
	&__area::-webkit-scrollbar {
		width: 5px;
	}

	::-webkit-scrollbar-track {
		background-color: rgb(255, 255, 255);
	}

	::-webkit-scrollbar-thumb {
		border-radius: 3px;
		box-shadow: inset 0 0 6px rgba(255, 140, 0, 0.3);
	}

	&__input {
		width: 100%;
		height: 65px;
		gap: 8px;
		padding: 0 10px;
		display: flex;
		justify-content: space-around;
	}

	&__buttons {
		z-index: 10;
		position: absolute;
		bottom: 76px;
		display: flex;
		gap: 10px;
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
