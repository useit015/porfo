<template>
	<div>
		<header class="header">
			<background/>
			<hello/>
		</header>
		<info/>
		<skills/>
		<work/>
		<contact/>
	</div>
</template>

<script>
	import info from "@/components/info";
	import work from "@/components/work";
	import hello from "@/components/hello";
	import skills from "@/components/skills";
	import contact from "@/components/contact";
	import background from "@/components/background";

	export default {
		components: {
			info,
			work,
			hello,
			skills,
			contact,
			background
		}
	};
</script>

<style scoped>
.header {
	height: 100vh;
}
</style>
