<template>
	<app-header></app-header>
	<RouterView />
</template>

<script>
import { RouterLink, RouterView } from "vue-router";
import AppHeader from "./components/Header.vue";

export default {
	name: "App",
	components: {
		AppHeader,
	},
};
</script>

<style>
body {
	margin: 0;
}
#app {
	max-width: 100%;
	margin: 0 auto;
	padding: 0;
	font-weight: normal;
}
</style>
