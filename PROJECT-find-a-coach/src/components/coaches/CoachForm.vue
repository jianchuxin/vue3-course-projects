<template>
	<form @submit.prevent="submitForm">
		<div class="form-control" :class="{ invalid: !validity.first }">
			<label for="firstName">名字</label>
			<input
				type="text"
				id="firstName"
				v-model="firstName"
				@blur="clearValidity('first')"
			/>
			<p v-if="!validity.first">名字不能为空!</p>
		</div>

		<div class="form-control" :class="{ invalid: !validity.last }">
			<label for="lastName">姓</label>
			<input
				type="text"
				id="lastName"
				v-model="lastName"
				@blur="clearValidity('last')"
			/>
			<p v-if="!validity.last">姓不能为空!</p>
		</div>

		<div class="form-control" :class="{ invalid: !validity.desc }">
			<label for="description">简介</label>
			<textarea
				id="description"
				rows="5"
				v-model="description"
				@blur="clearValidity('desc')"
			></textarea>
			<p v-if="!validity.desc">简介不能为空!</p>
		</div>

		<div class="form-control" :class="{ invalid: !validity.rate }">
			<label for="rate">时薪</label>
			<input
				type="number"
				id="rate"
				v-model="rate"
				@blur="clearValidity('rate')"
			/>
			<p v-if="!validity.rate">时薪应大于 0.</p>
		</div>

		<div class="form-control" :class="{ invalid: !validity.areas }">
			<h3>擅长技术领域</h3>
			<div>
				<input
					type="checkbox"
					id="frontend"
					value="frontend"
					v-model="areas"
					@blur="clearValidity('areas')"
				/>
				<label for="frontend">前端（Frontend）</label>
			</div>
			<div>
				<input
					type="checkbox"
					id="backend"
					value="backend"
					v-model="areas"
					@blur="clearValidity('areas')"
				/>
				<label for="backend">后端（backend）</label>
			</div>
			<div>
				<input
					type="checkbox"
					id="career"
					value="career"
					v-model="areas"
					@blur="clearValidity('areas')"
				/>
				<label for="career">全栈（Career Full Stack）</label>
			</div>
			<p v-if="!validity.areas">选择不少于1个</p>
		</div>
		<p v-if="!formIsValid">请修正错误填写，再次提交~</p>
		<base-button>提交</base-button>
	</form>
</template>

<script>
export default {
	emits: ['save-data'],
	data() {
		return {
			firstName: '',
			lastName: '',
			description: '',
			rate: null,
			areas: [],
			formIsValid: true,
			validity: {
				first: true,
				last: true,
				desc: true,
				rate: true,
				areas: true,
			},
		};
	},

	methods: {
		clearValidity(input) {
			this.validity[input] = true;
		},

		validateForm() {
			this.formIsValid = true;
			// this.validity.first = true;
			// this.validity.last = true;
			// this.validity.desc = true;
			// this.validity.rate = true;
			// this.validity.areas = true;

			if (this.firstName.trim() === '') {
				this.validity.first = false;
			}
			if (this.lastName.trim() === '') {
				this.validity.last = false;
			}
			if (this.description.trim() === '') {
				this.validity.desc = false;
			}
			if (!this.rate || this.rate < 0) {
				this.validity.rate = false;
			}
			if (this.areas.length === 0) {
				this.validity.areas = false;
			}

			for (const isValid of Object.values(this.validity)) {
				if (!isValid) {
					this.formIsValid = false;
					break;
				}
			}
		},
		submitForm() {
			this.validateForm();
			if (!this.formIsValid) {
				return;
			}
			const formData = {
				first: this.firstName,
				last: this.lastName,
				desc: this.description,
				rate: this.rate,
				areas: this.areas,
			};
			// console.log(formData);
			this.$emit('save-data', formData);
		},
	},
};
</script>

<style scoped>
.form-control {
	margin: 0.5rem 0;
}

label {
	font-weight: bold;
	display: block;
	margin-bottom: 0.5rem;
}

input[type='checkbox'] + label {
	font-weight: normal;
	display: inline;
	margin: 0 0 0 0.5rem;
}

input,
textarea {
	display: block;
	width: 100%;
	border: 1px solid #ccc;
	font: inherit;
}

input:focus,
textarea:focus {
	background-color: #e6fcf5;
	outline: none;
	border-color: #96f2d7;
}

input[type='checkbox'] {
	display: inline;
	width: auto;
	border: none;
}

input[type='checkbox']:focus {
	outline: #e6fcf5 solid 1px;
}

h3 {
	margin: 0.5rem 0;
	font-size: 1rem;
}

.invalid label {
	color: red;
}

.invalid input,
.invalid textarea {
	border: 1px solid red;
}
</style>
