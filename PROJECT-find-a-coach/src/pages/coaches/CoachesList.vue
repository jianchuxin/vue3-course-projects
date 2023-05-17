<template>
	<section>
		<coach-filter @change-filter="setFilters"></coach-filter>
	</section>
	<section>
		<base-card>
			<div class="controls">
				<base-button mode="flat">刷新</base-button>
				<base-button link="true" to="/register" v-if="!isRegistered"
					>注册成为教练</base-button
				>
			</div>
			<ul v-if="hasCoaches">
				<coach-item
					v-for="coach in filteredCoaches"
					:key="coach.id"
					:id="coach.id"
					:first-name="coach.firstName"
					:last-name="coach.lastName"
					:rate="coach.hourlyRate"
					:areas="coach.areas"
				></coach-item>
			</ul>
			<h3 v-else>暂时没有教练信息~</h3>
		</base-card>
	</section>
</template>

<script>
import CoachItem from '../../components/coaches/CoachItem.vue';
import CoachFilter from '../../components/coaches/CoachFilter.vue';
export default {
	components: {
		CoachItem,
		CoachFilter,
	},
	data() {
		return {
			activeFilters: ['frontend', 'backend', 'career'],
		};
	},
	computed: {
		isRegistered() {
			return this.$store.getters['coaches/isRegistered'];
		},
		filteredCoaches() {
			const coaches = this.$store.getters['coaches/coaches'];
			return coaches.filter((coach) => {
				for (const area of this.activeFilters) {
					if (coach.areas.includes(area)) {
						return true;
					}
				}
				return false;
			});
		},
		hasCoaches() {
			return this.$store.getters['coaches/hasCoaches'];
		},
	},
	methods: {
		setFilters(filters) {
			this.activeFilters = filters;
		},
	},
};
</script>

<style scoped>
.controls {
	display: flex;
	justify-content: space-between;
}
</style>
