<template>
	<header>
		<nav>
			<h1><router-link to="/">寻找一个教练</router-link></h1>
			<ul>
				<li><router-link to="/coaches">教练</router-link></li>
				<li><router-link to="/requests">请求</router-link></li>
			</ul>
		</nav>
	</header>
</template>

<script>
export default {};
</script>

<style scoped>
header {
	width: 100%;
	height: 5rem;
	background-color: #0ca678;
	/* background-image: linear-gradient(to left, #0ca678, #ffec99); */
	display: flex;
	justify-content: center;
	align-items: center;
}

header a {
	font-size: 1.4rem;
	color: #ffec99;
	text-decoration: none;
	display: inline-block;
	padding: 0.75rem 1.5rem;
}

a:active,
a:hover,
a.router-link-active {
	outline: 1px solid #ffec99;
}

h1 a {
	font-size: 2rem;
	color: #fff;
}

h1 a:hover,
h1 a:active,
h1 a.router-link-active {
	outline: transparent;
}

header nav {
	width: 90%;
	height: 100%;
	display: flex;
	justify-content: space-between;
	align-items: center;
}

header ul {
	list-style: none;
	display: flex;
	justify-content: center;
	align-items: center;
}

li {
	margin: 0 1rem;
}
</style>
