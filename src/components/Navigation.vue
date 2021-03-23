<template>
	<div>
		<nav class="navbar">
			<div class="container-fluid">
				<router-link class="navbar-brand" to="/">VideoChat App</router-link> |
				<div class="mr-auto">
					<span class="navbar-item mr-auto pl-3">
						<router-link to="">About</router-link>
					</span>
				</div>
				<span class="navbar-item pl-3">
					<router-link to="/host">Host a Meeting</router-link>
				</span>
				<span class="navbar-item pl-3">
					<router-link to="/login">Log In</router-link>
				</span>
			</div>
		</nav>
	</div>
</template>
