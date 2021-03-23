<template>
	<div class="row">
		<div class="col-4"></div>
		<div class="col-4">
			<div class="spacing"></div>
			<form class="mx-6">
				<div class="form-group">
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
					<label>Password</label>
					<input type="password" class="form-control" v-model="password" />
				</div>
				<button @click.prevent="login()" class="btn btn-primary">Submit</button>
				<div class="spacing"></div>
				<div style="color: red" v-if="error">{{ error }}</div>
				<p>or <router-link to="/register">Sign Up</router-link></p>
			</form>
		</div>
		<div class="col-4"></div>
	</div>
</template>

<script>
import Firebase from "firebase";
export default {
	name: "Login",
	data: function() {
		return {
			email: null,
			password: null,
			error: null,
		};
	},
	methods: {
		login: function() {
			const info = {
				email: this.email,
				password: this.password,
			};
			Firebase.auth()
				.signInWithEmailAndPassword(info.email, info.password)
				.then(
					() => {
						this.$router.push("/");
					},
					(error) => {
						this.error = error.message;
					},
				);
		},
	},
};
</script>
