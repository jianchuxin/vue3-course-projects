<template>
	<the-header title="RememberMe"></the-header>
	<the-resources></the-resources>
</template>

<script>
import TheHeader from "./components/layouts/TheHeader.vue";
import TheResources from "./components/learning-resources/TheResources.vue";
export default {
	components: {
		TheHeader,
		TheResources,
	},
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@500;600;700&display=swap");
* {
	box-sizing: border-box;
	margin: 0;
	padding: 0;
}

html {
	font-family: "Inter", sans-serif;
	font-size: 62.5%;
}
</style>
