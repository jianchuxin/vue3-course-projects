<template>
	<li>
		<h3>{{ fullName }}</h3>
		<h4>${{ rate }}/小时</h4>
		<div>
			<base-badge
				v-for="area in areas"
				:key="area"
				:type="area"
				:title="area"
			></base-badge>
		</div>
		<div class="actions">
			<base-button mode="outline" link="true" :to="coachContactLink"
				>联系</base-button
			>
			<base-button link="true" :to="coachDetailedLink"
				>详细信息</base-button
			>
		</div>
	</li>
</template>

<script>
export default {
	props: ['id', 'firstName', 'lastName', 'rate', 'areas'],
	computed: {
		fullName() {
			return this.firstName + ' ' + this.lastName;
		},
		coachContactLink() {
			return this.$route.path + '/' + this.id + '/contact';
		},
		coachDetailedLink() {
			return this.$route.path + '/' + this.id;
		},
	},
};
</script>

<style scoped>
li {
	list-style: none;
	margin-top: 1rem;
	border: 0;
	border-top: 1px solid #999;
	padding: 1rem;
}

h3 {
	font-size: 1.5rem;
}

h3,
h4 {
	margin: 0.5rem 0;
}

div {
	margin: 0.5rem 0;
}

.actions {
	display: flex;
	justify-content: flex-end;
	margin-top: 1rem;
}
</style>
