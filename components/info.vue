<template>
	<section class="about">
		<div class="container">
			<h2 class="subtitle">{{ `— ${$t('title.about')}` }}</h2>
			<p class="text" v-for="i in [0, 1, 2, 3]" :key="i">{{ $t(`content.about[${i}]`) }}</p>
			<div class="social__container">
				<svg-icon class="social__icon" v-for="icon in social" :key="icon" :name="icon"/>
			</div>
		</div>
	</section>
</template>

<script>
	export default {
		data: () => ({
			social: ['github', 'twitter', 'linkedin']
		})
	}
</script>


<style scoped>
	.about {
		width: 100vw;
		overflow: hidden;
		position: relative;
	}

	.social__container {
		display: flex;
		justify-content: space-evenly;
		align-items: center;
	}

	.social__icon {
		cursor: pointer;
		width: 70px;
		height: 70px;
		margin: 5vh 0 -2vh 0;
	}
</style>
