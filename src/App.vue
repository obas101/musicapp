<template>
	<div id="app">
		<div class="main">
			<div>
				<div class="header"><span class="headtext">Music</span></div>
			</div>
			<div class="large-spacing"></div>

			<div class="title">
				<span class="title">Music Title</span>
			</div>
			<div class="small-spacing"></div>
			<div class="control">
				<button id="small-button">Prev</button>
				<button id="large-button">Play</button>
				<button id="small-button">Next</button>
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
	font-family: Segoe UI;
	padding: 0;
	margin: 0;
}
#app {
	height: 100vh;
}
.header {
	background: black;
	color: white;
	text-align: center;
	padding: 1.5rem;
}
.control {
	display: flex;
	justify-content: center;
}
.large-spacing {
	margin-top: 4rem;
	width: 100%;
}
.small-spacing {
	margin-top: 2rem;
	width: 100%;
}
.title {
	font-size: 3rem;
	text-align: center;
	font-weight: 500;
}
.headtext {
	font-size: 2.5rem;
	font-weight: 700;
	letter-spacing: 6px;
}
button {
	margin-left: 1.5rem;
	margin-right: 1.5rem;
	border-radius: 8px;
	outline: none;
	border-color: thistle;
}
#small-button {
	background: #ff4587;
	color: white;
	font-size: 14px;
	font-weight: 700;
	padding: 0.4rem 1.2rem 0.4rem 1.2rem !important;
}
#large-button {
	background: #ff0076;
	color: white;
	font-size: 20px;
	font-weight: 700;
	padding: 0.8rem 1.8rem 0.8rem 1.8rem !important;
}
</style>
