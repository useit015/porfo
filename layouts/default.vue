<template>
	<div>
		<nuxt class="app"/>
	</div>
</template>

<style>
html {
	font-family: "Roboto", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
		"Segoe UI", "Helvetica Neue", Arial, sans-serif;
	font-size: 10px;
	word-spacing: 1px;
	-ms-text-size-adjust: 100%;
	-webkit-text-size-adjust: 100%;
	-moz-osx-font-smoothing: grayscale;
	-webkit-font-smoothing: antialiased;
	box-sizing: border-box;
	color: #283646;
	overflow-x: hidden;
}

*,
*:before,
*:after {
	box-sizing: border-box;
	margin: 0;
}

.app {
	background-image: linear-gradient(210deg, #84fab0 0%, #8fd3f4 100%);
	letter-spacing: 2px;
	line-height: 1.2;
}

.container {
	width: 70vw;
	max-width: 65rem;
	margin: 0 auto;
	padding-left: 1rem;
}

.subtitle {
	font-weight: 700;
	word-spacing: 10px;
	font-size: 5rem;
	margin-bottom: 4rem;
}

.text {
	margin: 1rem 0;
	line-height: 2;
	font-size: 1.68rem;
}

section {
	padding: 10rem 0;
}
</style>
