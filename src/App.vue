<template>
	<div id="app">
		<Navigation :user="user" @logout="logout" />
		<router-view :user="user" @logout="logout" />
	</div>
</template>

<script>
import Firebase from "firebase";
import Navigation from "./components/Navigation";
import db from "./db";

export default {
	name: "App",
	data: function() {
		return {
			user: null,
		};
	},
	methods: {
		logout: function() {
			Firebase.auth()
				.signOut()
				.then(() => {
					(this.user = null), this.$router.push("/login");
				});
		},
	},
	mounted() {
		Firebase.auth().onAuthStateChanged((user) => {
			if (user) {
				this.user = user;
				console.log("user :", user);
			}
		});
	},
	components: {
		Navigation,
	},
};
</script>

<style lang="scss">
$primary: #0c65a4;
@import "node_modules/bootstrap/scss/bootstrap";
.spacing {
	margin-top: 3rem;
}
</style>
