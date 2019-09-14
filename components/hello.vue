<template>
	<!-- <div class="container"> -->
	<h1 class="title">Hello.</h1>
	<!-- <h2 class="subtitle">
			I'm a Freelance
			<br />Developer.
	</h2>-->
	<!-- <p class="text">I'm a student from 1337, a pretty cool computer science school from the 42 Network in Khouribga, Morocco.</p>
		<p class="text">During the last four years, I've been working a lot with web technologies, mostly from the JavaScript ecosystem.</p>
		<p class="text">Architecture matters to me. Things have to stay clean and simple, and with this in mind I take time creating modules and boilerplates, trying to bring some purity in my work.</p>
		<p class="text">Graphic Design is also something I care about. I've been working by the past on multiple graphic design projects, like logo, serigraphy or webdesign.</p>
	<div class="links"></div>-->
	<!-- </div> -->
</template>

<style scoped>
	.title {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		color: #fff;
		font-size: 10rem;
		font-weight: 700;
		letter-spacing: 4px;
		text-align: center;
	}

	.title::before,
	.title::after {
		content: "";
		position: absolute;
		width: 100px;
		height: 200px;
		background: url(~assets/dot.png);
		background-size: 25px;
		opacity: 0.4;
	}

	.title::before {
		top: 120%;
		right: 80%;
	}

	.title::after {
		bottom: 110%;
		left: 80%;
	}

	@media screen and (max-width: 55em) {
		.title::before,
		.title::after {
			width: 50px;
			height: 100px;
			background-size: 12px;
		}
	}
</style>
