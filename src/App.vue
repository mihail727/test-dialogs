<script setup lang="ts">
import AppLayout from '@/containers/AppLayout.vue';
</script>

<template>
	<div :class="$style.appContainer">
		<AppLayout>
			<RouterView v-slot="{ Component, route }">
				<component :is="Component" :key="route.fullPath" />
			</RouterView>
		</AppLayout>
	</div>
</template>

<style src="@/assets/scss/global/index.scss" />
<style lang="scss" module>
.appContainer {
	width: 100vw;
	height: 100vh;
}
</style>
