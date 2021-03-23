<template>
	<div>
		<h1>Home</h1>
		<p>Welcome {{ this.user }}</p>
	</div>
</template>

<script>
import db from "../db";
export default {
	name: "home",
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
};
</script>
