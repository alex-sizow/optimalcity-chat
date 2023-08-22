<script setup lang="ts">
import { ref } from 'vue';

import ChatInput from './ChatInput.vue';

defineProps<{ msg: string; rt: string }>();

const count = ref(0);
</script>

<template>
	<div class="chat">
		<div class="chat__area">
			<div class="avatar">
				<div class="avatar__icon">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						width="30"
						height="30">
						<path
							d="M4.953 8.844H.328c-.02 2.441 1.734 3.582 4.625 3.582Zm0 0"
							style="
								stroke: none;
								fill-rule: nonzero;
								fill: #ffbf67;
								fill-opacity: 1;
							" />
						<path
							d="M5.117 12.59h-.164c-1.762 0-3.062-.414-3.867-1.223-.621-.625-.93-1.472-.922-2.523l.004-.164h4.95ZM.497 9.012c.023.883.3 1.593.823 2.12.715.723 1.883 1.102 3.47 1.126V9.012Zm0 0"
							style="
								stroke: none;
								fill-rule: nonzero;
								fill: #28272c;
								fill-opacity: 1;
							" />
						<path
							d="M15.266 13.82a6.101 6.101 0 0 0 1.379-3.879A6.143 6.143 0 0 0 10.5 3.797 6.144 6.144 0 0 0 4.352 9.94a6.13 6.13 0 0 0 1.234 3.688c-2.332 7.48 2.973 12.906 12.523 12.523 6.364-.254 11.528-6.695 11.528-14.957-3.832 2.375-8.399 3.602-14.371 2.625Zm0 0"
							style="
								stroke: none;
								fill-rule: nonzero;
								fill: #ffd57f;
								fill-opacity: 1;
							" />
						<path
							d="M18.766 19.516a.163.163 0 0 1-.164-.153.164.164 0 0 1 .136-.175c4.239-.633 7.328-2.704 9.73-6.516a.166.166 0 0 1 .145-.082.168.168 0 0 1 .145.09.162.162 0 0 1-.012.168c-2.422 3.847-5.68 6.027-9.957 6.664-.008.004-.016.004-.023.004Zm0 0"
							style="
								stroke: none;
								fill-rule: nonzero;
								fill: #28272c;
								fill-opacity: 1;
							" />
						<path
							d="M18.11 26.152C8.558 26.535 3.253 21.11 5.585 13.63A6.13 6.13 0 0 1 4.352 9.94 6.144 6.144 0 0 1 10.5 3.797c-1.422 11.285 1.816 18.062 7.61 22.355Zm0 0"
							style="
								stroke: none;
								fill-rule: nonzero;
								fill: #ffbf67;
								fill-opacity: 1;
							" />
						<path
							d="M17.152 26.336c-4.765 0-8.504-1.473-10.59-4.195-1.753-2.286-2.156-5.22-1.156-8.48a6.26 6.26 0 0 1-1.218-3.72c0-3.48 2.832-6.312 6.308-6.312A6.32 6.32 0 0 1 16.81 9.94a6.312 6.312 0 0 1-1.243 3.758c5.246.805 9.82-.062 13.985-2.644l.25-.157v.297c0 8.215-5.133 14.86-11.684 15.121-.324.012-.648.02-.965.02ZM10.5 3.96a5.99 5.99 0 0 0-5.984 5.98c0 1.301.418 2.54 1.203 3.59l.05.067-.023.078c-.996 3.191-.625 6.047 1.078 8.265 2.156 2.817 6.164 4.258 11.281 4.047 6.297-.254 11.243-6.597 11.364-14.496-4.235 2.547-8.895 3.363-14.23 2.488l-.278-.043.176-.222A5.983 5.983 0 0 0 16.48 9.94a5.988 5.988 0 0 0-5.98-5.98Zm0 0"
							style="
								stroke: none;
								fill-rule: nonzero;
								fill: #28272c;
								fill-opacity: 1;
							" />
						<path
							d="M7.578 8.254a.597.597 0 0 1-.594.598.6.6 0 0 1-.597-.598.597.597 0 0 1 1.191 0Zm0 0"
							style="
								stroke: none;
								fill-rule: nonzero;
								fill: #28272c;
								fill-opacity: 1;
							" />
						<path
							d="M6.984 9.016a.763.763 0 0 1-.761-.762.759.759 0 1 1 .762.762Zm0-1.192a.43.43 0 0 0-.414.43c0 .234.184.422.414.434a.432.432 0 0 0 0-.863Zm0 0"
							style="
								stroke: none;
								fill-rule: nonzero;
								fill: #28272c;
								fill-opacity: 1;
							" />
					</svg>
				</div>
				<span class="avatar__description">Duck bot</span>
			</div>
			<div class="message">
				<div style="--n: 53">
					Lorem ipsum dolor sit amet consectetur adipisicing
					elit. Nisi, magnam?
				</div>
				<div style="--n: 53">
					Lorem ipsum dolor sit amet consectetur adipisicing
					elit. Nisi, magnam?
				</div>
			</div>
		</div>
		<div class="chat__input">
			<chat-input />
			<button class="chat__input_button">
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
	gap: 20px;
	padding-top: 12px;

	&__area {
		width: 92%;
		height: 100%;
		display: flex;
		flex-direction: column;
		gap: 10px;
		padding: 10px;

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
				box-shadow: 3px 3px 6px #f2f2f2, -3px -3px 6px #ffffff;
				animation: fadeIn 0.5s;
			}
			&__description {
				animation: fadeIn 1s;
			}
		}
		.message {
			display: flex;
			flex-direction: column;
			gap: 5px;
			animation: fadeIn 4s;
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
				box-shadow: 1px 1px 1px #6dcddc, -1px -1px 1px #79e3f4;
			}
			margin-left: 21px;
			:first-child {
				border-radius: 0px 25px 25px 12px;
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
