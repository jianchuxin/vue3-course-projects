<template>
	<teleport to="html">
		<div @click="$emit('close')"></div>
		<dialog open>
			<header>
				<slot name="header">
					<h2>{{ title }}</h2>
				</slot>
			</header>
			<section>
				<slot></slot>
			</section>
			<menu>
				<slot name="action">
					<base-button @click="$emit('close')">Close</base-button>
				</slot>
			</menu>
		</dialog>
	</teleport>
</template>

<script>
export default {
	// props: ["title"],
	emits: ["close"],
	props: {
		title: {
			type: String,
			required: false,
		},
	},
};
</script>
<style scoped>
div {
	position: fixed;
	top: 0;
	left: 0;
	height: 100vh;
	width: 100%;
	background-color: rgba(0, 0, 0, 0.75);
	backdrop-filter: blur(5px);
	z-index: 10;
}

dialog {
	position: fixed;
	top: 20vh;
	left: 50%;
	width: 80%;
	z-index: 100;
	transform: translateX(-50%);
	border: none;
	border-radius: 12px;
	overflow: hidden;
	z-index: 9999;
	max-width: 55rem;
}

header {
	background-color: #3a0061;
	color: #fff;
	width: 100%;
	padding: 2rem;
}

header h2 {
	font-size: 2rem;
}

section {
	padding: 2rem;
}

menu {
	padding: 2rem;
	display: flex;
	justify-content: flex-end;
	margin: 0;
}
</style>
