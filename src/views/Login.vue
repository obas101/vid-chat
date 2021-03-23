<template>
	<div class="row">
		<div class="col-3"></div>
		<div class="col-6">
			<div class="spacing"></div>
			<form class="mx-6" @submit.prevent="login">
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
				<button type="submit" class="btn btn-primary">Submit</button>
			</form>
		</div>
		<div class="col-3"></div>
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
		};
	},
	methods: {
		login: function() {
			const dataCollected = {
				email: this.email,
				password: this.password,
			};
			Firebase.auth()
				.signInWithEmailAndPassword(dataCollected.email, dataCollected.password)
				.then(() => {
					this.$router.push("/");
				});
		},
	},
};
</script>
