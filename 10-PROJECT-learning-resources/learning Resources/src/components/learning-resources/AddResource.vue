<template>
	<base-card>
		<form @submit.prevent="submitData">
			<div class="form-control">
				<label for="title">Title</label>
				<input
					id="title"
					name="title"
					type="text"
					v-model="enteredRes.title"
				/>
			</div>
			<div class="form-control">
				<label for="description">Description</label>
				<textarea
					id="description"
					name="description"
					type="text"
					rows="3"
					v-model="enteredRes.description"
				></textarea>
			</div>
			<div class="form-control">
				<label for="Link">Link</label>
				<input
					id="Link"
					name="Link"
					type="url"
					v-model="enteredRes.link"
				/>
			</div>
			<div>
				<base-button type="submit">Add resources</base-button>
			</div>
		</form>
	</base-card>
	<base-dialog
		v-if="inputIsInvid"
		title="Invaild Input"
		@close="confirmError"
	>
		<template v-slot:default>
			<p>please enter at least something... 😀</p>
			<p>
				please check all inputs and make sure you enter at least a few
				characters into each filed.
			</p>
		</template>
		<template v-slot:action>
			<base-button @click="confirmError">Okey</base-button>
		</template>
	</base-dialog>
</template>

<script>
export default {
	emits: ["submitRes"],

	data() {
		return {
			enteredRes: {
				title: "",
				description: "",
				link: "",
			},
			inputIsInvid: false,
		};
	},
	methods: {
		submitData() {
			if (
				this.enteredRes.title.trim() === "" ||
				this.enteredRes.description.trim() === "" ||
				this.enteredRes.link.trim() === ""
			) {
				this.inputIsInvid = true;
				return;
			}
			this.$emit("submitRes", this.enteredRes);
		},
		confirmError() {
			this.inputIsInvid = false;
		},
	},
};
</script>

<style scoped>
label {
	font-weight: bold;
	display: block;
	margin-bottom: 0.5rem;
}

input,
textarea {
	display: block;
	width: 100%;
	font: inherit;
	padding: 0.15rem;
	border: 1px solid #ccc;
}

input:focus,
textarea:focus {
	outline: none;
	border-color: #3a0061;
	background: #f7ebff;
}

.form-control {
	margin: 1rem 0;
}
</style>
