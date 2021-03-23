<template>
	<div>
		<nav class="navbar">
			<div class="container-fluid">
				<router-link class="navbar-brand" to="/">VideoChat App</router-link> |
				<div class="mr-auto">
					<span class="navbar-item pl-3 mr-3" v-if="user">
						Welcome {{ user.displayName }}
					</span>
				</div>
				<span class="navbar-item">
					<router-link to="/host">Host a Meeting</router-link>
				</span>

				<span class="navbar-item pl-3" v-if="!user">
					<router-link to="/login">Log In</router-link>
				</span>
				<span class="navbar-item pl-3" v-if="!user">
					<router-link to="/register">Register</router-link>
				</span>
				<span class="navbar-item pl-3" v-if="user">
					<button @click="$emit('logout')">Log Out</button>
				</span>
			</div>
		</nav>
	</div>
</template>
<script>
export default {
	name: "Navigation",
	props: ["user"],
};
</script>
