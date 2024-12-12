<script setup lang="ts">
import { ref } from 'vue';
import { vOnClickOutside } from '@vueuse/components';

const modalEl = ref<HTMLDialogElement | undefined>();

function onClickOpenModal() {
	modalEl.value?.showModal();
}

function onClickCloseModal() {
	modalEl.value?.close();
}
</script>

<template>
	<div :class="$style.homePage">
		<button :class="$style.button" @click="onClickOpenModal">Open Modal</button>

		<dialog ref="modalEl" :class="$style.modalContainer">
			<div v-on-click-outside="onClickCloseModal" :class="$style.modal">
				<h1>Some Modal Dialog</h1>
				<h2>Can be closed by button or ESC key</h2>
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
	height: 110dvh;
}

.button {
	padding: 10px;
	border-radius: 5px;
	background-color: black;
	color: white;
	border: 1px solid white;
}

.modalContainer {
	padding: 0;
	border: 0;

	&::backdrop {
		background-color: rgba(0, 0, 0, 0.5);
	}
}

.modal {
	display: flex;
	flex-direction: column;
	background-color: red;
}
</style>
