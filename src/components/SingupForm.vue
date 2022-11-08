<template>
	<aside>
		<div class="wrapper">
			<div class="tryout-free">
				<p><span>Try it free 7 days</span> then $20/mo. thereafter</p>
			</div>
			<form @submit="validateForm">
				<div>
					<input
						@blur="validateFirstName"
						:class="[
							errors.includes('firstName')
								? 'input-form-error'
								: 'input-form',
						]"
						type="text"
						name="first-name"
						v-model="firstName"
						placeholder="First Name"
					/>
					<span
						id="firstName-error"
						:class="{
							'input-form-label-error':
								errors.includes('firstName'),
						}"
					/>
				</div>

				<div>
					<input
						@blur="validateLastName"
						:class="[
							errors.includes('lastName')
								? 'input-form-error'
								: 'input-form',
						]"
						type="text"
						name="last-name"
						v-model="lastName"
						placeholder="Last Name"
					/>
					<span
						id="lastName-error"
						:class="{
							'input-form-label-error':
								errors.includes('lastName'),
						}"
					/>
				</div>

				<div>
					<input
						@blur="validateEmail"
						:class="[
							errors.includes('email')
								? 'input-form-error'
								: 'input-form',
						]"
						type="text"
						name="email"
						v-model="email"
						placeholder="Email Adrress"
					/>
					<span
						id="email-error"
						:class="{
							'input-form-label-error': errors.includes('email'),
						}"
					/>
				</div>

				<div>
					<input
						@blur="validatePassword"
						:class="[
							errors.includes('password')
								? 'input-form-error'
								: 'input-form',
						]"
						type="password"
						name="password"
						v-model="password"
						placeholder="password"
					/>
					<span
						id="password-error"
						:class="{
							'input-form-label-error':
								errors.includes('password'),
						}"
					/>
				</div>
				<div>
					<button class="submit-button" type="submit">
						CLAIM YOUR FREE TRIAL
					</button>
					<span class="terms-services">
						By clicking the button, you are agreeing to our
						<span>Terms and Services</span>
					</span>
				</div>
			</form>
		</div>
	</aside>
</template>

<script>
import $ from "jquery";

export default {
	name: "SingupForm",
	data() {
		return {
			errors: [],
			firstName: "",
			lastName: "",
			email: "",
			password: "",
		}
	},
	methods: {
		validateForm: function (e) {
			this.errors = [];

			this.validateFirstName();
			this.validateLastName();
			this.validateEmail();
			this.validatePassword();

			if (this.errors.length === 0){
				return true;
			}

			e.preventDefault();
		},
		validateFirstName: function () {
			this.errors = this.errors.filter(input => input != 'firstName');

			if (!this.firstName) {
				this.errors.push("firstName")
                $("#firstName-error").text("Por favor, insira seu primeiro nome");
			} else {
                $("#firstName-error").text("");
			}
		},
		validateLastName: function () {
			this.errors = this.errors.filter(input => input != 'lastname');

			if (!this.lastName) {
				this.errors.push("lastName")
                $("#lastName-error").text("Por favor, insira seu sobrenome");
			} else {
                $("#lastName-error").text("");
			}
		},
		validateEmail: function (email) {
			this.errors = this.errors.filter(input => input != 'email');
			let re = /^(([^<>()[\]\.,;:\s@\"]+(\.[^<>()[\]\.,;:\s@\"]+)*)|(\".+\"))@(([^<>()[\]\.,;:\s@\"]+\.)+[^<>()[\]\.,;:\s@\"]{2,})$/i;

			if (!this.email) {
				this.errors.push("email")
                $("#email-error").text("Por favor, insira um email válido");
			} else if (!re.test(this.email)) {
				this.errors.push("email")
				$("#email-error").text("Email inválido, ex: joao@gmail.com");
			} else {
				$("#email-error").text("");
			}
		},
		validatePassword: function (email) {
			this.errors = this.errors.filter(input => input != 'password');

			if (!this.password) {
				this.errors.push("password")
                $("#password-error").text("Por favor, insira uma senha");
			} else {
                $("#password-error").text("");
			}
		}
	}
};
</script>

<style scoped>
aside {
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: flex-start;
}

.wrapper {
	max-width: 38vw;
}

.tryout-free {
	width: 100%;

	background-color: var(--blue);
	border-style: none;
	border-radius: 10px;
	box-shadow: 0px 8px 0px rgba(0, 0, 0, 0.15);

	padding: 17px 67px;
	margin-bottom: 24px;

	font-weight: var(--regular);
	line-height: 26px;
	text-align: center;
}

.tryout-free > p > span {
	font-weight: var(--bold);
}

form {
	width: 100%;

	background-color: #fff;
	border-radius: 10px;
	box-shadow: 0px 8px 0px rgba(0, 0, 0, 0.15);

	display: flex;
	flex-direction: column;
	align-items: center;
	gap: 20px;

	padding: 55px 40px;
}

form > div {
	width: 100%;
}

.input-form {
	width: 100%;

	padding: 15px 32px;

	border: 2px solid hsla(0, 0%, 87%, 1);
	border-radius: 5px;

	color: black;

	transition: all 200ms;
}

.input-form:focus,
.input-form:hover {
	border: 2px solid var(--dark-blue);
}

.input-form-error {
	width: 100%;

	padding: 15px 32px;

	border: 2px solid var(--red);
	border-radius: 5px;

	background: url("../assets/icon-error.svg") no-repeat;
	background-position: 95%;

	color: black;

	transition: all 200ms;
}

.input-form-label-error {
	display: block;

	color: var(--red);

	width: 100%;

	font-size: var(--small);
	font-style: italic;
	text-align: end;
}

.submit-button {
	width: 100%;

	background-color: var(--green);
	border-style: none;
	border-radius: 10px;
	box-shadow: inset 0px -4px 0px rgba(0, 0, 0, 0.15);

	padding: 15px;

	font-weight: var(--semibold);
	line-height: 26px;

	cursor: pointer;

	transition: all 150ms;
}

.submit-button:hover {
	background-color: var(--almost-green);
}

form > div {
	text-align: center;
}

.terms-services {
	width: 100%;

	padding: 0 10px 0 10px;

	color: var(--almost-white);
	font-size: var(--small);
	font-weight: var(--medium);

	transition: all 150ms;
}

.terms-services > span {
	color: var(--almost-orange);
	font-weight: var(--semibold);
}

.terms-services > span:hover {
	cursor: pointer;
	text-shadow: 0px 1px 1px rgba(0, 0, 0, 0.25);
}

@media (max-width: 920px) {
	aside {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.wrapper {
		min-width: 70vw;
	}

	form {
		gap: 16px;

		padding: 24px;
	}
}

@media (max-width: 640px) {
	aside {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.wrapper {
		min-width: 90vw;
	}

	form {
		gap: 16px;

		padding: 24px;
	}
}
</style>
