<template>
	<div class="row">
		<div class="col-4"></div>
		<div class="col-4">
			<div class="spacing"></div>
			<form class="mx-6">
				<div class="form-group">
					<label>Username</label>
					<input type="name" class="form-control" v-model="displayName" />
					<label>Email address</label>
					<input
						type="email"
						class="form-control"
						aria-describedby="emailHelp"
						v-model="email"
					/>
					<small class="form-text text-muted"
						>We'll never share your email with anyone else.</small
					>
				</div>
				<div class="form-group">
					<div class="row">
						<div class="col-6">
							<label>Password</label>
							<input type="password" class="form-control" v-model="passOne" />
						</div>
						<div class="col-6">
							<label>ReEnter Password</label>
							<input type="password" class="form-control" v-model="passTwo" />
						</div>
					</div>
				</div>
				<button @click.prevent="register" class="btn btn-primary">
					Register
				</button>
				<div class="spacing"></div>
				<div style="color: red" v-if="error">{{ error }}</div>
				<p>or <router-link to="/login">Log In</router-link></p>
			</form>
		</div>
		<div class="col-4"></div>
	</div>
</template>

<script>
import Firebase from "firebase";
export default {
	name: "Register",
	data: function() {
		return {
			displayName: null,
			email: null,
			passOne: null,
			passTwo: null,
			error: null,
		};
	},
	methods: {
		register: function() {
			const info = {
				displayName: this.displayName,
				email: this.email,
				password: this.passTwo,
			};
			if (!this.error) {
				Firebase.auth()
					.createUserWithEmailAndPassword(info.email, info.password)
					.then(
						(userCredentials) => {
							return userCredentials.user
								.updateProfile({
									displayName: info.displayName,
								})
								.then(() => {
									this.$router.replace("/");
								});
						},
						(error) => {
							this.error = error.message;
						},
					);
			}
		},
	},
	watch: {
		passTwo: function() {
			if (
				this.passOne !== "" &&
				this.passTwo !== "" &&
				this.passOne !== this.passTwo
			) {
				this.error = "Password must match";
			} else {
				this.error = null;
			}
		},
	},
};
</script>
