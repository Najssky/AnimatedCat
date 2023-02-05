<template>
	<div class="container">
		<catSigns
			:canFeedTheCat="canFeedTheCat"
			:catFeeded="catFeeded"
		></catSigns>
		<div class="cat">
			<div class="catHead">
				<div class="leftEar"><div class="leftInsideEar"></div></div>
				<div class="rightEar"><div class="rightInsideEar"></div></div>
				<div class="leftEye"></div>
				<div class="nose"></div>
				<div class="rightEye"></div>
				<div class="mouth">
					<div
						class="upLine"
						v-if="!canFeedTheCat || catFeeded"
					></div>
					<div class="leftLine" v-if="!canFeedTheCat"></div>
					<div class="rightLine" v-if="!canFeedTheCat"></div>
					<div
						class="openMouth"
						v-if="canFeedTheCat && !catFeeded"
					></div>
					<div class="happyLeftLine" v-if="catFeeded"></div>
					<div class="happyRightLine" v-if="catFeeded"></div>
				</div>
			</div>
			<div class="catBody">
				<div class="paw"></div>
				<div class="paw"></div>
				<div class="paw"></div>
				<div class="paw"></div>
				<div class="tail">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						version="1.1"
						xmlns:xlink="http://www.w3.org/1999/xlink"
						xmlns:svgjs="http://svgjs.dev/svgjs"
						viewBox="0 0 800 400"
					>
						<path
							d="M283.85650634765625,187.44393920898438C325.71002197265625,188.0418497721354,356.2032979329427,158.74439493815103,409.41705322265625,189.2376708984375C462.6308085123698,219.73094685872397,432.1375325520833,249.02840169270834,443.4977722167969,278.92376708984375"
							fill="none"
							stroke-width="41"
							stroke=" #ff7a00"
							stroke-linecap="round"
							transform="matrix(-0.8252131812420254,-0.8126763387750153,-0.8379434247120472,0.5386196510232092,892.092622970604,374.0781883580503)"
							stroke-dasharray="125 0"
							stroke-opacity="1"
						></path>
						<defs>
							<linearGradient id="SvgjsLinearGradient1002">
								<stop
									stop-color="hsl(37, 99%, 67%)"
									offset="0"
								></stop>
								<stop
									stop-color="hsl(316, 73%, 52%)"
									offset="1"
								></stop>
							</linearGradient>
						</defs>
					</svg>
				</div>
			</div>
		</div>
		<div class="catBowl">
			<img class="bowl" :src="imageSource" />
		</div>
		<button
			class="primary feedBtn"
			@click="feedTheCat()"
			:disabled="!canFeedTheCat"
		>
			<b>FEED THE CAT</b>
		</button>
	</div>
</template>

<script>
import catSigns from "./catSigns.vue";

export default {
	data() {
		return {
			imageSource: "https://i.imgur.com/NkxIGVz.png",
			catFeeded: false,
			canFeedTheCat: false,
		};
	},
	components: {
		catSigns,
	},
	name: "animatedCat",
	methods: {
		feedTheCat() {
			this.imageSource = "https://i.imgur.com/bWyxDmx.png";
			this.catFeeded = true;
		},
		waitForCat() {
			setTimeout(() => (this.canFeedTheCat = true), 8250);
		},
	},
	created() {
		this.waitForCat();
	},
};
</script>

<style>
* {
	margin: 0;
	padding: 0;
}
@keyframes catWalk {
	0% {
		transform: rotate(0deg);
	}
	50% {
		transform: rotate(-30deg);
	}
	100% {
		transform: rotate(0deg);
	}
}
@media only screen and (min-width: 1001px) {
	.container {
		height: 500px;
		max-width: 1920px;
		background: rgba(0, 140, 255, 0.582);
		margin-left: 0;
		overflow: hidden;
	}
	.cat {
		position: relative;
		animation-name: catBodyMove;
		animation-duration: 8.25s;
		animation-delay: 0.5;
		animation-iteration-count: 1;
		animation-fill-mode: forwards;
	}

	.catHead {
		background: #ff7a00;
		height: 100px;
		width: 125px;
		border-radius: 25px;
		position: absolute;
		top: 50px;
	}
	.leftEar,
	.rightEar {
		border-left: 20px solid transparent;
		border-right: 20px solid transparent;
		border-bottom: 25px solid #ff7a00;
		height: 0;
		width: 0;
		position: relative;
	}
	.leftEar {
		top: -24px;
		left: calc(25% - 10px);
	}
	.rightEar {
		top: -49px;
		left: calc(50% + 5px);
	}
	.leftInsideEar,
	.rightInsideEar {
		position: relative;
		border-left: 10px solid transparent;
		border-right: 10px solid transparent;
		border-bottom: 15px solid #ff4fa1;
	}
	.leftInsideEar {
		top: 10px;
		left: -10px;
	}
	.rightInsideEar {
		top: 10px;
		left: -10px;
	}
	.leftEye,
	.rightEye {
		position: relative;
		width: 20px;
		height: 20px;
		background: black;
		border-radius: 20px;
		border: solid 5px brown;
	}
	.leftEye {
		top: -30px;
		left: calc(25% - 15px);
	}
	.rightEye {
		top: -70px;
		left: calc(75% - 15px);
	}
	.nose {
		width: 0;
		height: 0;
		position: relative;
		top: -30px;
		left: calc(50% - 10px);
		border-left: 10px solid transparent;
		border-right: 10px solid transparent;
		border-top: 10px solid #ff4fa1;
		z-index: 1;
	}
	.upLine {
		height: 15px;
		width: 1px;
		position: relative;
		top: -65px;
		left: calc(50% - 0.5px);
		background: black;
	}
	.leftLine,
	.rightLine {
		width: 1px;
		height: 10px;
		background: black;
		position: relative;
	}
	.leftLine {
		transform: rotate(45deg);
		top: -67px;
		left: calc(50% - 4px);
	}
	.rightLine {
		transform: rotate(-45deg);
		top: -77px;
		left: calc(50% + 3px);
	}
	.happyLeftLine,
	.happyRightLine {
		width: 1px;
		height: 10px;
		background: black;
		position: relative;
	}
	.happyLeftLine {
		transform: rotate(-45deg);
		top: -72px;
		left: calc(50% - 4px);
	}
	.happyRightLine {
		transform: rotate(45deg);
		top: -82px;
		left: calc(50% + 3px);
	}
	.openMouth {
		width: 30px;
		height: 15px;
		position: relative;
		top: -57px;
		left: calc(50% - 16px);
		border: 1px solid black;
		border-radius: 50%;
	}
	.catBody {
		width: 225px;
		height: 100px;
		background: #ff7a00;
		position: absolute;
		left: -125px;
		top: 150px;
		border-top-left-radius: 80px;
		border-bottom-right-radius: 10px;
	}
	.paw {
		width: 15px;
		height: 35px;
		background: #ff7a00;
		position: relative;
		border-bottom-left-radius: 5px;
		border-bottom-right-radius: 5px;
	}
	.paw:nth-child(1) {
		top: 95px;
		left: 195px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-iteration-count: 5;
	}
	.paw:nth-child(2) {
		top: 60px;
		left: 160px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-delay: 0.75s;
		animation-iteration-count: 5;
	}
	.paw:nth-child(3) {
		top: 25px;
		left: 45px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-iteration-count: 5;
	}
	.paw:nth-child(4) {
		top: -10px;
		left: 10px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-delay: 0.75s;
		animation-iteration-count: 5;
	}
	.tail {
		position: relative;
		top: -150px;
		left: -130px;
	}
	.bowl {
		width: 150px;
		position: absolute;
		top: 350px;
		left: 1025px;
	}
	.feedBtn {
		padding: 10px;
		position: absolute;
		top: 300px;
		left: 1045px;
		background: lightblue;
	}
	.feedBtn:hover {
		cursor: pointer;
	}

	@keyframes catBodyMove {
		0% {
			top: 170px;
			left: 200px;
		}
		100% {
			top: 170px;
			left: 900px;
		}
	}
}
@media only screen and (min-width: 641px) and (max-width: 1000px) {
	.container {
		height: 250px;
		max-width: 1000px;
		background: rgba(0, 140, 255, 0.582);
		margin-left: 0;
		overflow: hidden;
	}
	.cat {
		position: relative;
		animation-name: catBodyMove;
		animation-duration: 8.25s;
		animation-delay: 0.5;
		animation-iteration-count: 1;
		animation-fill-mode: forwards;
	}

	.catHead {
		background: #ff7a00;
		height: 50px;
		width: 62.5px;
		border-radius: 12.5px;
		position: absolute;
		top: 25px;
	}
	.leftEar,
	.rightEar {
		border-left: 10px solid transparent;
		border-right: 10px solid transparent;
		border-bottom: 12px solid #ff7a00;
		height: 0;
		width: 0;
		position: relative;
	}
	.leftEar {
		top: -12px;
		left: calc(25% - 5px);
	}
	.rightEar {
		top: -24.5px;
		left: calc(50% + 2.5px);
	}
	.leftInsideEar,
	.rightInsideEar {
		position: relative;
		border-left: 5px solid transparent;
		border-right: 5px solid transparent;
		border-bottom: 7.5px solid #ff4fa1;
	}
	.leftInsideEar {
		top: 5px;
		left: -5px;
	}
	.rightInsideEar {
		top: 5px;
		left: -5px;
	}
	.leftEye,
	.rightEye {
		position: relative;
		width: 10px;
		height: 10px;
		background: black;
		border-radius: 10px;
		border: solid 2.5px brown;
	}
	.leftEye {
		top: -15px;
		left: calc(25% - 7.5px);
	}
	.rightEye {
		top: -35px;
		left: calc(75% - 7.5px);
	}
	.nose {
		width: 0;
		height: 0;
		position: relative;
		top: -15px;
		left: calc(50% - 5px);
		border-left: 5px solid transparent;
		border-right: 5px solid transparent;
		border-top: 5px solid #ff4fa1;
		z-index: 1;
	}
	.upLine {
		height: 7.5px;
		width: 1px;
		position: relative;
		top: -32.5px;
		left: calc(50% - 0.25px);
		background: black;
	}
	.leftLine,
	.rightLine {
		width: 1px;
		height: 5px;
		background: black;
		position: relative;
	}
	.leftLine {
		transform: rotate(45deg);
		top: -33.5px;
		left: calc(50% - 2px);
	}
	.rightLine {
		transform: rotate(-45deg);
		top: -38.5px;
		left: calc(50% + 1.5px);
	}
	.happyLeftLine,
	.happyRightLine {
		width: 1px;
		height: 5px;
		background: black;
		position: relative;
	}
	.happyLeftLine {
		transform: rotate(-45deg);
		top: -36px;
		left: calc(50% - 2px);
	}
	.happyRightLine {
		transform: rotate(45deg);
		top: -41px;
		left: calc(50% + 1.5px);
	}
	.openMouth {
		width: 15px;
		height: 7.5px;
		position: relative;
		top: -28.5px;
		left: calc(50% - 8px);
		border: 1px solid black;
		border-radius: 50%;
	}
	.catBody {
		width: 112.5px;
		height: 50px;
		background: #ff7a00;
		position: absolute;
		left: -62.5px;
		top: 75px;
		border-top-left-radius: 40px;
		border-bottom-right-radius: 5px;
	}
	.paw {
		width: 7.5px;
		height: 17.5px;
		background: #ff7a00;
		position: relative;
		border-bottom-left-radius: 2.5px;
		border-bottom-right-radius: 2.5px;
	}
	.paw:nth-child(1) {
		top: 47.5px;
		left: 97.5px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-iteration-count: 5;
	}
	.paw:nth-child(2) {
		top: 30px;
		left: 80px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-delay: 0.75s;
		animation-iteration-count: 5;
	}
	.paw:nth-child(3) {
		top: 12.5px;
		left: 22.5px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-iteration-count: 5;
	}
	.paw:nth-child(4) {
		top: -5px;
		left: 5px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-delay: 0.75s;
		animation-iteration-count: 5;
	}
	.tail {
		position: relative;
		top: -75px;
		left: -65px;
	}
	.bowl {
		width: 75px;
		position: absolute;
		top: 175px;
		left: 512.5px;
	}
	.feedBtn {
		padding: 5px;
		position: absolute;
		top: 150px;
		left: 522.5px;
		background: lightblue;
	}
	.feedBtn:hover {
		cursor: pointer;
	}

	@keyframes catBodyMove {
		0% {
			top: 85px;
			left: 100px;
		}
		100% {
			top: 85px;
			left: 450px;
		}
	}
}
@media only screen and (max-width: 640px) {
	.container {
		height: 500px;
		max-width: 640px;
		background: rgba(0, 140, 255, 0.582);
		margin-left: 0;
		overflow: hidden;
	}
	.cat {
		position: relative;
		animation-name: catBodyMove;
		animation-duration: 8.25s;
		animation-delay: 0.5;
		animation-iteration-count: 1;
		animation-fill-mode: forwards;
	}

	.catHead {
		background: #ff7a00;
		height: 33.3px;
		width: 41.6px;
		border-radius: 8.3px;
		position: absolute;
		top: 16.6px;
	}
	.leftEar,
	.rightEar {
		border-left: 6.3px solid transparent;
		border-right: 6.3px solid transparent;
		border-bottom: 8.3px solid #ff7a00;
		height: 0;
		width: 0;
		position: relative;
	}
	.leftEar {
		top: -8px;
		left: calc(25% - 3.3px);
	}
	.rightEar {
		top: -16.3px;
		left: calc(50% + 1.3px);
	}
	.leftInsideEar,
	.rightInsideEar {
		position: relative;
		border-left: 3.3px solid transparent;
		border-right: 3.3px solid transparent;
		border-bottom: 5px solid #ff4fa1;
	}
	.leftInsideEar {
		top: 3.3px;
		left: -3.3px;
	}
	.rightInsideEar {
		top: 3.3px;
		left: -3.3px;
	}
	.leftEye,
	.rightEye {
		position: relative;
		width: 6.6px;
		height: 6.6px;
		background: black;
		border-radius: 6.6px;
		border: solid 1.3px brown;
	}
	.leftEye {
		top: -10px;
		left: calc(25% - 5px);
	}
	.rightEye {
		top: -21.3px;
		left: calc(75% - 5px);
	}
	.nose {
		width: 0;
		height: 0;
		position: relative;
		top: -10px;
		left: calc(50% - 3.3px);
		border-left: 3.3px solid transparent;
		border-right: 3.3px solid transparent;
		border-top: 3.3px solid #ff4fa1;
		z-index: 1;
	}
	.upLine {
		height: 5px;
		width: 1px;
		position: relative;
		top: -21.6px;
		left: calc(50% - 1px);
		background: black;
	}
	.leftLine,
	.rightLine {
		width: 1px;
		height: 3.3px;
		background: black;
		position: relative;
	}
	.leftLine {
		transform: rotate(45deg);
		top: -22.3px;
		left: calc(50% - 2.3px);
	}
	.rightLine {
		transform: rotate(-45deg);
		top: -26px;
		left: calc(50%);
	}
	.happyLeftLine,
	.happyRightLine {
		width: 1px;
		height: 3.3px;
		background: black;
		position: relative;
	}
	.happyLeftLine {
		transform: rotate(-45deg);
		top: -22px;
		left: calc(50% - 2px);
	}
	.happyRightLine {
		transform: rotate(45deg);
		top: -25.7px;
		left: calc(50% - 0px);
	}
	.openMouth {
		width: 8px;
		height: 5px;
		position: relative;
		top: -17px;
		left: calc(50% - 6px);
		border: 1px solid black;
		border-radius: 50%;
	}
	.catBody {
		width: 75px;
		height: 33.3px;
		background: #ff7a00;
		position: absolute;
		left: -41.6px;
		top: 49.6px;
		border-top-left-radius: 26.6px;
		border-bottom-right-radius: 3.3px;
	}
	.paw {
		width: 5px;
		height: 11.3px;
		background: #ff7a00;
		position: relative;
		border-bottom-left-radius: 1.3px;
		border-bottom-right-radius: 1.3px;
	}
	.paw:nth-child(1) {
		top: 31.3px;
		left: 65px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-iteration-count: 5;
	}
	.paw:nth-child(2) {
		top: 20px;
		left: 53.3px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-delay: 0.75s;
		animation-iteration-count: 5;
	}
	.paw:nth-child(3) {
		top: 8.3px;
		left: 15px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-iteration-count: 5;
	}
	.paw:nth-child(4) {
		top: -3.3px;
		left: 3.3px;
		animation-name: catWalk;
		animation-duration: 1.5s;
		animation-delay: 0.75s;
		animation-iteration-count: 5;
	}
	.tail {
		position: relative;
		top: -50px;
		left: -43.3px;
	}
	.bowl {
		width: 50px;
		position: absolute;
		top: 116.6px;
		left: 341.6px;
	}
	.feedBtn {
		padding: 3.3px;
		position: absolute;
		top: 200px;
		left: 40%;
		background: lightblue;
	}
	.feedBtn:hover {
		cursor: pointer;
	}
	@keyframes catBodyMove {
		0% {
			top: 56.6px;
			left: 66.6px;
		}
		100% {
			top: 56.6px;
			left: 300px;
		}
	}
}
</style>
