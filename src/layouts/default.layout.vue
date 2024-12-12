<script setup lang="ts"></script>

<template>
	<div :class="$style.defaultLayout">
		<slot />
	</div>
</template>

<style lang="scss" module>
.defaultLayout {
	width: 375px;
	justify-self: center;
}
</style>
