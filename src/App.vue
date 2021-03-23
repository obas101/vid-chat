<template>
	<div id="app">
		<Navigation :user="user" />
		<router-view :user="user" />
	</div>
</template>

<script>
import Navigation from "./components/Navigation";
import db from "./db";

export default {
	name: "App",
	data: function() {
		return {
			user: null,
		};
	},
	mounted() {
		db.collection("users")
			.doc("n5ynKjvWUd2achkHudeZ")
			.get()
			.then((snapshot) => {
				this.user = snapshot.data().name;
			});
		console.log("name:", this.user);
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
