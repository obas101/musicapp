<template>
	<div id="app">
		<div class="main">
			<div>
				<div class="header"><span class="headtext">Music</span></div>
			</div>
			<div class="small-spacing"></div>
			<div class="display">
				<div class="title-main">
					<span class="title">{{ current.title }} - </span>
					<span class="artist">{{ current.artist }}</span>
				</div>
				<div class="small-spacing"></div>
				<div class="control">
					<button class="small-button" @click="prev">Prev</button>
					<button class="large-button" v-if="!isPlaying" @click="play">
						Play
					</button>
					<button class="large-button" v-else @click="pause">Pause</button>
					<button class="small-button" @click="next">Next</button>
				</div>
			</div>
			<div class="display-2">
				<div class="large-spacing"></div>
				<div class="playlist">Playlist</div>
				<div class="small-spacing"></div>
				<div class="ddd">
					<button
						class="ddd1"
						v-for="song in songs"
						:key="song.src"
						@click="play(song)"
						:class="song.src == current.src ? 'song playing' : 'song'"
					>
						{{ song.title }} - {{ song.artist }}}
					</button>
				</div>
			</div>
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
	padding: 1.3rem;
}
.control {
	display: flex;
	justify-content: center;
}
.playlist {
	text-align: center;
	font-size: 1.8rem;
	font-weight: 700;
}
.large-spacing {
	margin-top: 3.5rem;
	width: 100%;
}
.small-spacing {
	margin-top: 1.5rem;
	width: 100%;
}
.title-main {
	text-align: center;
}
.display {
	position: fixed;
	width: 100%;
}
.display-2 {
	position: relative;
	top: 10rem;
}
.title {
	font-size: 3rem;
	text-align: center;
	font-weight: 600;
}
.artist {
	font-size: 2.5rem;
	font-weight: 500;
	font-style: italic;
}
.headtext {
	font-size: 2.5rem;
	font-weight: 700;
	letter-spacing: 6px;
}
.small-button {
	background: #ff4587;
	color: white;
	font-size: 13px;
	font-weight: 700;
	width: 4rem;
	padding-top: 0.5rem;
	padding-bottom: 0.5rem;
	margin-top: 0.8rem;
	margin-bottom: 0.8rem;
	/* padding: 0.4rem 1.2rem 0.4rem 1.2rem !important; */
	margin-left: 1.5rem;
	margin-right: 1.5rem;
	border-radius: 8px;
	outline: none;
	border-color: thistle;
	cursor: pointer;
}
.large-button {
	background: #ff0076;
	color: white;
	font-size: 20px;
	font-weight: 700;
	width: 7rem;
	padding-top: 1rem;
	padding-bottom: 1rem;
	/* padding: 0.8rem 1.8rem 0.8rem 1.8rem !important; */
	margin-left: 1.5rem;
	margin-right: 1.5rem;
	border-radius: 8px;
	outline: none;
	border-color: thistle;
	cursor: pointer;
}
.ddd1 {
	display: block;
	width: 100%;
	/* justify-content: center; */
	cursor: pointer;
	/* width: 80%; */
	/* text-align: center; */
	padding: 1rem;
	/* justify-content: center; */
	/* margin-right: 2rem; */
	background: white;
	border: none;
	outline: none;

	font-size: 20px;
	font-weight: 700;
}
.ddd1:hover {
	background: rgb(255, 69, 135);
	border: none;
	outline: none;
	color: white;
}
.ddd {
	padding: 0rem 5rem;
	outline: none;
	border: none;
}
</style>
