<template>
	<form @submit.prevent="submitForm">
		<div class="form-control">
			<label for="email">你的邮件</label>
			<input type="email" id="email" v-model="email" />
		</div>

		<div class="form-control">
			<label for="message">内容</label>
			<textarea id="message" rows="5" v-model="message"></textarea>
		</div>
		<p class="errors" v-if="!formIsValid">请输入有效的邮箱以及非空内容</p>
		<div class="actions">
			<base-button>发送</base-button>
		</div>
	</form>
</template>

<script>
export default {
	data() {
		return {
			email: '',
			message: '',
			formIsValid: true,
		};
	},

	methods: {
		submitForm() {
			this.fromIsValid = true;
			if (
				this.email.trim() === '' ||
				!this.email.includes('@') ||
				this.message.trim() === ''
			) {
				this.formIsValid = false;
				return;
			}
			this.$store.dispatch('requests/addRequest', {
				email: this.email,
				message: this.message,
				coachId: this.$route.params.id,
			});
			this.$router.replace('/coaches');
		},
	},
};
</script>

<style scoped>
form {
	margin: 1rem;
	border: 1px solid #ccc;
	border-radius: 12px;
	padding: 1rem;
}

.form-control {
	margin: 0.5rem 0;
}

label {
	font-weight: bold;
	margin-bottom: 0.5rem;
	display: block;
}

input,
textarea {
	display: block;
	width: 100%;
	font: inherit;
	border: 1px solid #ccc;
	padding: 0.15rem;
}

input:focus,
textarea:focus {
	border-color: #96f2d7;
	background-color: #e6fcf5;
	outline: none;
}

.errors {
	font-weight: bold;
	color: red;
}

.actions {
	text-align: center;
}
</style>
