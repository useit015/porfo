<template>
	<h1 class="title">Hello.</h1>
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
