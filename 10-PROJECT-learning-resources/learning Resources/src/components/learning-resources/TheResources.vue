<template>
	<base-card>
		<base-button
			@click="setSelectedTab('stored-resources')"
			:mode="storedButtonMode"
			>Stored Resources</base-button
		>
		<base-button
			@click="setSelectedTab('add-resource')"
			:mode="addButtonMode"
			>Add Resource</base-button
		>
	</base-card>
	<!-- <stored-resources
		v-if="selectedTab === 'stored-resources'"
	></stored-resources>
	<add-resource
		v-if="selectedTab === 'add-resource'"
		@submitRes="addRes"
	></add-resource> -->
	<keep-alive>
		<component :is="selectedTab" @submitRes="addRes"></component>
	</keep-alive>
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource.vue";
export default {
	components: {
		StoredResources,
		AddResource,
	},
	data() {
		return {
			selectedTab: "stored-resources",
			storedResources: [
				{
					id: "off-guide",
					title: "Official Guide",
					description: "The official Vue.js documentation",
					link: "https://cn.vuejs.org/",
				},
				{
					id: "google",
					title: "Google",
					description: "Learn to google...",
					link: "https://google.com",
				},
			],
		};
	},
	provide() {
		return {
			resources: this.storedResources,
			removeRes: this.removeRes,
		};
	},
	methods: {
		setSelectedTab(tab) {
			this.selectedTab = tab;
		},
		addRes(res) {
			res.id = new Date().toISOString();
			if (res.title === "") {
				return;
			} else {
				this.storedResources.unshift(res);
				console.log(res);
				this.selectedTab = "stored-resources";
			}
		},
		removeRes(resId) {
			// this.storedResources = this.storedResources.filter((res) => {
			// 	return res.id !== resId;
			// });
			const resIndex = this.storedResources.findIndex((res) => {
				return res.id === resId;
			});
			this.storedResources.splice(resIndex, 1);
		},
	},
	computed: {
		storedButtonMode() {
			return this.selectedTab === "stored-resources" ? null : "flat";
		},
		addButtonMode() {
			return this.selectedTab === "add-resource" ? null : "flat";
		},
	},
};
</script>
