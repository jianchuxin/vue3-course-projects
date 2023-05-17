<template>
	<span class="badge" :class="type"> {{ text }}</span>
</template>

<script>
export default {
	props: ['type', 'title'],
	computed: {
		text() {
			return this.title.toUpperCase();
		},
	},
};
</script>

<style scoped>
.badge {
	background-color: #ccc;
	color: #212529;
	border-radius: 12px;
	padding: 0.5rem 1.5rem;
	display: inline-block;
	margin-right: 0.5rem;
}

.frontend {
	background-color: #0ca678;
	color: white;
}

.backend {
	background-color: #f59f00;
	color: white;
}

.career {
	background-color: #4263eb;
	color: white;
}
</style>
