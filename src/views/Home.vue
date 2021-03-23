<template>
	<div>
		<div class="row">
			<div class="col-3"></div>
			<div class="col-6 text-style">
				<div class="spacing"></div>
				<p>Welcome {{ this.user }}</p>

				<h1>Video Chat</h1>
				<p>
					This app uses Firebase for real-time communication and WebRTC to
					create video chat between multiple users, allowing you to create rooms
					for meeting and invite people to join meetings.
				</p>
				<router-link class="btn btn-primary" to="/login">Log In</router-link>
			</div>
			<div class="col-3"></div>
		</div>
	</div>
</template>

<script>
export default {
	name: "home",
	props: ["user"],
};
</script>
<style scoped>
.text-style {
	text-align: center;
}
</style>
