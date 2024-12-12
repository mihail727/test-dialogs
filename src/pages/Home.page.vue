<script setup lang="ts">
import { ref } from 'vue';

const modalEl = ref<HTMLDialogElement | undefined>();

function onClickOpenModal() {
	modalEl.value?.showModal();
}

function onClickCloseModal() {
	modalEl.value?.close();
}

function onModalClick(ev: Event) {
	const isClickedOutside = ev.target === ev.currentTarget;

	if (isClickedOutside) {
		modalEl.value?.close();
	}
}
</script>

<template>
	<div :class="$style.homePage">
		<button :class="$style.button" @click="onClickOpenModal">Open Modal</button>

		<dialog ref="modalEl" :class="$style.modal" @click="onModalClick">
			<div :class="$style.modalContent">
				<h1>Some Modal Dialog</h1>
				<h2>Can be closed by button or ESC key</h2>
				<input type="text" />
				<button :class="$style.button" @click="onClickCloseModal">Close</button>
			</div>
		</dialog>
	</div>
</template>

<style lang="scss" module>
.homePage {
	display: flex;
	flex-direction: column;
	padding: 20px 0 20px 0;
	// height: 110dvh;
}

.button {
	padding: 10px;
	border-radius: 5px;
	background-color: black;
	color: white;
	border: 1px solid white;
}

.modal {
	padding: 0;
	border: 0;
	animation: fade-out 0.7s ease-out;

	&[open] {
		animation: fade-in 0.7s ease-out;

		&::backdrop {
			animation: backdrop-fade-in 0.7s ease forwards;
		}
	}

	&::backdrop {
		background-color: rgba(0, 0, 0, 0.5);
	}

	@keyframes fade-in {
		0% {
			opacity: 0;
			transform: translateY(-100%);
			display: none;
		}

		100% {
			opacity: 1;
			transform: translateY(0%);
			display: block;
		}
	}

	@keyframes fade-out {
		0% {
			opacity: 1;
			transform: translateY(0%);
			display: block;
		}

		100% {
			opacity: 0;
			transform: translateY(-100%);
			display: none;
		}
	}
}

.modalContent {
	display: flex;
	flex-direction: column;
	border: 1px solid white;
	background-color: black;
	color: white;
}
</style>
