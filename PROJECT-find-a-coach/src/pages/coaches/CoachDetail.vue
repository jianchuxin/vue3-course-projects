<template>
	<section>
		<base-card>
			<h2>{{ fullName }}</h2>
			<h3>${{ rate }}/小时</h3>
		</base-card>
	</section>
	<section>
		<base-card>
			<header>
				<h2>😊感兴趣? 立即联系！</h2>
				<base-button link :to="contactLink">联系ta</base-button>
			</header>
			<router-view></router-view>
		</base-card>
	</section>
	<section>
		<base-card>
			<base-badge
				v-for="area in areas"
				:key="area"
				:type="area"
				:title="area"
			></base-badge>
			<p>{{ description }}</p>
		</base-card>
	</section>
</template>

<script>
export default {
	props: ['id'],
	data() {
		return {
			seletedCoach: null,
		};
	},
	computed: {
		fullName() {
			return (
				this.seletedCoach.firstName + ' ' + this.seletedCoach.lastName
			);
		},
		contactLink() {
			return this.$route.path + '/contact';
		},
		areas() {
			return this.seletedCoach.areas;
		},
		rate() {
			return this.seletedCoach.hourlyRate;
		},
		description() {
			return this.seletedCoach.description;
		},
	},
	created() {
		this.seletedCoach = this.$store.getters['coaches/coaches'].find(
			(coach) => coach.id === this.id
		);
	},
};
</script>

<style scoped>
h2 {
	margin-bottom: 1.8rem;
}

p {
	margin: 1.6rem 0;
	line-height: 1.4;
}
</style>
