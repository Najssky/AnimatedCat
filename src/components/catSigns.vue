<template>
	<div>
		<div class="hearts" v-if="catFeeded">
			<div class="heart" v-for="index in 3" :key="index"></div>
		</div>
		<div class="meows" v-if="!catFeeded">
			<span class="meow" v-for="index in 3" :key="index">MEOW!</span>
		</div>
	</div>
</template>

<script>
export default {
	name: "catSigns",
	props: ["catFeeded", "canFeedTheCat"],
};
</script>

<style>
@keyframes heartbeat {
	0% {
		transform: scale(0.75);
	}
	25% {
		transform: scale(1);
	}
	50% {
		transform: scale(0.75);
	}
	75% {
		transform: scale(1);
	}
	100% {
		transform: scale(0.75);
	}
}
@keyframes meowing {
	0% {
		transform: scale(0);
		opacity: 0;
	}
	50% {
		transform: scale(1);
		opacity: 1;
	}
	60% {
		transform: scale(0);
		opacity: 0;
	}
	100% {
		transform: scale(0);
		opacity: 0;
	}
}
@media only screen and (min-width: 1001px) {
	.heart {
		border-radius: 50px 50px 0 0;
		position: absolute;
		height: 50px;
		width: 50px;
		animation-name: heartbeat;
		animation-duration: 1s;
		animation-iteration-count: infinite;
	}
	.heart:before,
	.heart:after {
		position: absolute;
		content: "";
		left: 25px;
		top: 0;
		width: 25px;
		height: 40px;
		background: #ff0000;
		border-radius: 25px 25px 0 0;
		transform: rotate(-45deg);
		transform-origin: 0 100%;
	}
	.heart:after {
		left: 0;
		transform: rotate(45deg);
		transform-origin: 100% 100%;
	}
	.heart:nth-child(1) {
		left: 890px;
		top: 150px;
	}
	.heart:nth-child(2) {
		left: 940px;
		top: 100px;
	}

	.heart:nth-child(3) {
		top: 150px;
		left: 990px;
	}
	.meow {
		position: absolute;
		font-weight: bold;
		font-family: Tahoma, sans-serif;
		animation-name: meowing;
		animation-duration: 1s;
		animation-iteration-count: infinite;
		opacity: 0;
	}
	.meow:nth-child(1) {
		left: 890px;
		top: 150px;
		animation-delay: 8.5s;
	}
	.meow:nth-child(2) {
		left: 940px;
		top: 120px;
		animation-delay: 8.8s;
	}
	.meow:nth-child(3) {
		top: 150px;
		left: 990px;
		animation-delay: 9.1s;
	}
}
@media only screen and (min-width: 641px) and (max-width: 1000px) {
	.heart {
		border-radius: 25px 25px 0 0;
		position: absolute;
		height: 25px;
		width: 25px;
		animation-name: heartbeat;
		animation-duration: 1s;
		animation-iteration-count: infinite;
	}
	.heart:before,
	.heart:after {
		position: absolute;
		content: "";
		left: 12.5px;
		top: 0;
		width: 12.5px;
		height: 20px;
		background: #ff0000;
		border-radius: 12.5px 12.5px 0 0;
		transform: rotate(-45deg);
		transform-origin: 0 100%;
	}
	.heart:after {
		left: 0;
		transform: rotate(45deg);
		transform-origin: 100% 100%;
	}
	.heart:nth-child(1) {
		left: 445px;
		top: 75px;
	}
	.heart:nth-child(2) {
		left: 470px;
		top: 50px;
	}

	.heart:nth-child(3) {
		top: 75px;
		left: 495px;
	}
	.meow {
		position: absolute;
		font-weight: bold;
		font-family: Tahoma, sans-serif;
		font-size: 14px;
		animation-name: meowing;
		animation-duration: 1s;
		animation-iteration-count: infinite;
		opacity: 0;
	}
	.meow:nth-child(1) {
		left: 430px;
		top: 75px;
		animation-delay: 8.5s;
	}
	.meow:nth-child(2) {
		left: 455px;
		top: 60px;
		animation-delay: 8.8s;
	}
	.meow:nth-child(3) {
		top: 75px;
		left: 480px;
		animation-delay: 9.1s;
	}
}
@media only screen and (max-width: 640px) {
	.heart {
		border-radius: 16.6px 16.6px 0 0;
		position: absolute;
		height: 16.6px;
		width: 16.6px;
		animation-name: heartbeat;
		animation-duration: 1s;
		animation-iteration-count: infinite;
	}
	.heart:before,
	.heart:after {
		position: absolute;
		content: "";
		left: 8.3px;
		top: 0;
		width: 8.3px;
		height: 13.3px;
		background: #ff0000;
		border-radius: 8.3px 8.3px 0 0;
		transform: rotate(-45deg);
		transform-origin: 0 100%;
	}
	.heart:after {
		left: 0;
		transform: rotate(45deg);
		transform-origin: 100% 100%;
	}
	.heart:nth-child(1) {
		left: 300px;
		top: 50px;
	}
	.heart:nth-child(2) {
		left: 316.6px;
		top: 33.3px;
	}

	.heart:nth-child(3) {
		top: 50px;
		left: 333.3px;
	}
	.meow {
		position: absolute;
		font-weight: bold;
		font-family: Tahoma, sans-serif;
		animation-name: meowing;
		animation-duration: 1s;
		animation-iteration-count: infinite;
		opacity: 0;
		font-size: 8px;
	}
	.meow:nth-child(1) {
		left: 300px;
		top: 50px;
		animation-delay: 8.5s;
	}
	.meow:nth-child(2) {
		left: 316.6px;
		top: 40px;
		animation-delay: 8.8s;
	}
	.meow:nth-child(3) {
		top: 50px;
		left: 333.3px;
		animation-delay: 9.1s;
	}
}
</style>
