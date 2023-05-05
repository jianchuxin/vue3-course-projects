<template>
	<li>
		<base-card>
			<header>
				<h3>{{ title }}</h3>
				<base-button type="button" mode="flat" @click="removeRes(id)"
					>Delete</base-button
				>
			</header>
			<p>{{ description }}</p>
			<nav>
				<a :href="link">View Resource</a>
			</nav>
		</base-card>
	</li>
</template>

<script>
export default {
	props: ["id", "title", "description", "link"],
	inject: ["removeRes"],
};
</script>

<style scoped>
header {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin-bottom: 1rem;
}

header h3 {
	font-size: 1.8rem;
	color: #333;
	font-weight: 700;
}

p {
	font-size: 1.6rem;
	font-size: 500;
	color: #555;
	line-height: 1.2;
	margin-bottom: 1rem;
}

nav a:link,
nav a:visited {
	font-size: 1.4rem;
	text-decoration: none;
	color: #fd7e14;
	transform: all 0.3s;
}

nav a:hover,
nav a:active {
	color: #e8590c;
}
</style>
