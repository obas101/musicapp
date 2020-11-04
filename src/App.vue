<template>
	<div id="app">
		<div class="main">
			<div>
				<div class="header"><span class="headtext">Music</span></div>
			</div>
			<div class="large-spacing"></div>

			<div class="title">
				<span class="title">{{ current.title }} - {{ current.artist }}</span>
			</div>
			<div class="small-spacing"></div>
			<div class="control">
				<button id="small-button" @click="prev">Prev</button>
				<button id="large-button" v-if="!isPlaying" @click="play">
					Play
				</button>
				<button id="large-button" v-else @click="pause">Pause</button>
				<button id="small-button" @click="next">Next</button>
			</div>
			<div class="large-spacing"></div>
			<div class="playlist">Playlist</div>
			<div class="small-spacing"></div>
			<button
				v-for="song in songs"
				:key="song.src"
				@click="play(song)"
				:class="song.src == current.src ? 'song playing' : 'song'"
			>
				{{ song.title }} - {{ song.artist }}}
			</button>
		</div>
	</div>
</template>

<script>
export default {
	name: "App",
	components: {},
	data() {
		return {
			current: {},
			index: 0,
			isPlaying: false,
			songs: [
				{
					title: "Bad Influence",
					artist: "Omah Lay",
					src: require("./assets/Bad-Influence.mp3"),
				},
				{
					title: "Lo Lo",
					artist: "Omah Lay",
					src: require("./assets/Omah-Lay-Lo-Lo.mp3"),
				},
				{
					title: "You",
					artist: "Omah Lay",
					src: require("./assets/OmahLay-You.mp3"),
				},
			],
			player: new Audio(),
		};
	},
	methods: {
		play(song) {
			if (typeof song.src != "undefined") {
				this.current = song;
				this.player.src = this.current.src;
			}
			this.player.play();
			this.isPlaying = true;
		},
		pause() {
			this.player.pause();
			this.isPlaying = false;
		},
		next() {
			this.index++;
			if (this.index > this.songs.length - 1) {
				this.index = 0;
			}
			this.current = this.songs[this.index];
			this.play(this.current);
		},
		prev() {
			this.index--;
			if (this.index < 0) {
				this.index = this.songs.length - 1;
			}
			this.current = this.songs[this.index];
			this.play(this.current);
		},
	},
	created() {
		this.current = this.songs[this.index];
		this.player.src = this.current.src;
	},
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
.playlist {
	text-align: center;
	font-size: 2rem;
	font-weight: 600;
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
	font-size: 13px;
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
