<template>
	<div id="app">
		<div class="main">
			<div>
				<div class="header"><span class="headtext">MusicApp</span></div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "App",
	components: {},
};
</script>

<style>
* {
	padding: 0;
	margin: 0;
}
#app {
	height: 100vh;
}
.header {
	width: 100%;
	background: black;
	color: white;
	padding: 1.5rem;
  text-align: center;
}
.headtext {
	font-size: 2.5rem;
	font-weight: 700;
}
</style>
