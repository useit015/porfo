<template>
	<div>
		<header class="header">
			<background />
			<hello />
		</header>
		<section class="about">
			<div class="container">
				<h2 class="subtitle">
					— I'm Oussama Nahiz,
					<br />a freelance developer & designer.
				</h2>
				<p
					class="text"
				>I'm a student from 1337, a pretty cool computer science school from the 42 Network in Khouribga, Morocco.</p>
				<p
					class="text"
				>I've always been drawn to the overlap between design and development. My skills are broad: from ux to design, front end to back end development.</p>
				<p
					class="text"
				>Architecture matters to me. Things have to stay clean and simple, and with this in mind I take time creating modules and boilerplates, trying to bring some purity in my work.</p>
				<p
					class="text"
				>I'm available for remote work - if you would like to build something together, get in touch?</p>
				<div class="links"></div>
			</div>
		</section>
		<skills />
	</div>
</template>

<script>
	import hello from "@/components/hello";
	import background from "@/components/background";
	import skills from "@/components/skills";

	export default {
		components: {
			skills,
			hello,
			background
		}
	};
</script>

<style scoped>
	.header {
		height: 100vh;
	}

	.about {
		width: 100vw;
		overflow: hidden;
		letter-spacing: 2px;
		line-height: 1.2;
	}

	.container {
		width: 70%;
		max-width: 65rem;
		margin: 0 auto;
		padding-left: 1rem;
	}

	.subtitle {
		font-weight: 700;
		word-spacing: 10px;
		font-size: 3.5rem;
		margin-bottom: 3rem;
	}

	.text {
		margin: 1rem 0;
		line-height: 2;
		font-size: 1.68rem;
	}

	.links {
		padding-top: 15px;
	}
</style>
