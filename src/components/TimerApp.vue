<template>
	<div class="body">
		<h1 class="logo">
			<span class="online">Timer</span>
			<span class="vue">Vue</span>
		</h1>
		<div>
			<div class="timer">
				<div class="timer-display">
					<p><span v-if="hourse < 10">0</span>{{ hourse }}</p>
					<span class="">:</span>
					<p><span v-if="minutes < 10">0</span>{{ minutes }}</p>
					<span>:</span>
					<p><span v-if="seconds < 10">0</span>{{ seconds }}</p>
				</div>
				<div class="btns-container">
					<my-buttons v-if="visibleBtn" class="item" @click="startTimer"><svg class="start"
							xmlns="http://www.w3.org/2000/svg" width="800" height="800" viewBox="-7 0 32 32">
							<path d="M0 6.688v18.906c0 
								.344.156.625.469.813.125.094.344.125.5.125s.281-.031.438-.125l16.375-9.438c.313-.219.5-.5.5-.844 
								0-.313-.188-.594-.5-.813L1.407 
								5.874c-.563-.406-1.406.094-1.406.813z" />
						</svg></my-buttons>
					<my-buttons v-else class="item" @click="stopTimer">
						<svg class="stop" xmlns="http://www.w3.org/2000/svg" width="800" height="800" viewBox="-5.5 0 32 32">
							<path
								d="M0 6.563v18.875c0 .531.438.969.969.969h6.625c.5 0 
								.906-.438.906-.969V6.563c0-.531-.406-.969-.906-.969H.969A.974.974 0 0 0 0 6.563zm12.281 0v18.875c0 
								.531.438.969.938.969h6.625a.974.974 0 0 0 .969-.969V6.563a.974.974 0 0 0-.969-.969h-6.625c-.5 0-.938.438-.938.969z" />
						</svg>
					</my-buttons>
					<my-buttons class="item" @click="clearTimer"><svg class="clear" xmlns="http://www.w3.org/2000/svg" width="800"
							height="800" viewBox="0 0 16 16">
							<path d="M5.233.494a8 8 0 0 1 8.22 1.652l.84-.84c.63-.63 1.707-.184 1.707.707V6h-3.987c-.891 
								0-1.337-1.077-.707-1.707l.731-.732a6 6 0 1 0 1.378 7.024 1 1 0 0 1 1.805.861A8 8 0 1 1 5.233.494Z" />
						</svg></my-buttons>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import MyButtons from "./MyButtons.vue";
export default {
	components: { MyButtons },
	name: "timer-app",
	data() {
		return {
			visibleBtn: true,
			timer: null,
			hourse: 0,
			minutes: 0,
			seconds: 0,
		};
	},
	methods: {
		startTimer() {
			this.visibleBtn = false;
			this.timer = setInterval(() => {
				if (this.seconds > 59) {
					this.seconds = 0;
					this.minutes++;
					if (this.minutes > 59) {
						this.minutes = 0;
						this.hourse++;
					}
				}
				this.seconds++;
			}, 1000);
		},
		stopTimer() {
			this.visibleBtn = true;
			clearInterval(this.timer);
		},
		clearTimer() {
			this.seconds = 0;
			this.minutes = 0;
			this.hourse = 0;
		},
	},
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Quicksand&family=Raleway&display=swap");

.body {
	width: 800px;
	margin: 30px auto;
	padding: 20px;
	background-color: #fff;
	box-shadow: 0 0 50px #ccc;
	border: 1px solid #c7c7c7;
	position: relative;
	border-radius: 5px;
}

.logo {
	display: flex;
	align-items: center;
	font-family: "Raleway", sans-serif;
	font-weight: 400;
	font-size: 64px;
	line-height: 64px;
	margin: 5px;
}

.logo .online {
	color: #a52a2a8f;
}

.logo .vue {
	color: violet;
}

.timer {
	display: flex;
	padding: 20px 0;
	flex-direction: row;
	justify-content: center;
}

.timer-display {
	color: #c000ff;
	display: flex;
	font-size: 130px;
	line-height: 130px;
}

.timer-display p {
	font-family: "Quicksand", sans-serif;
	border: none;
	box-shadow: none;
	width: 150px;
	height: 120px;
	text-align: center;
	color: #c000ff;
	text-shadow: #999 1px 1px 5px;
}

.btns-container {
	height: 129px;
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	margin-left: 60px;
}

.item {
	display: flex;
	justify-content: center;
	align-items: center;
	width: 55px;
	height: 55px;
	background-color: #bf00ff6f;
	border: 2px solid #bf00ff6f;
	transition: ease .6s;
}

.item:hover {
	background-color: #bf00ff;
}

.start {
	width: 45px;
	height: 45px;
	fill: antiquewhite;
}

.stop {
	width: 45px;
	height: 45px;
	fill: antiquewhite;
}

.clear {
	width: 35px;
	height: 35px;
	fill: antiquewhite;
}
</style>