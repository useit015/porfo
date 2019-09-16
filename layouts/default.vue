<template>
	<div>
		<nuxt class="app"/>
	</div>
</template>

<style>
:root {
	--color-primary: #84fab0;
	--color-accent: #8fd3f4;
	--color-dark: #283646;
	--color-light: #c8e8ec;
}

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
	background-image: linear-gradient(
		210deg,
		var(--color-primary) 0%,
		var(--color-accent) 100%
	);
	letter-spacing: 2px;
	line-height: 1.2;
}

body::-webkit-scrollbar {
	width: 1rem;
}

body::-webkit-scrollbar-track {
	box-shadow: inset -1rem 0 2rem #89e7d1cc;
}

body::-webkit-scrollbar-thumb {
	background-color: var(--color-dark);
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
