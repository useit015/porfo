<template>
	<section class="projects">
		<div class="container">
			<h2 class="subtitle">{{ `— ${$t('title.work')}` }}</h2>
			<ul class="projects__list">
				<li
					v-for="(project, i) in projects"
					:key="i"
					@mouseover="hoverIn(i)"
					@mouseleave="hoverOut()"
					class="projects__item"
				>
					<span class="projects__roman">{{ `${romans[i]}.` }}</span>
					<span class="projects__text">{{ project.text }}</span>
				</li>
				<img
					:src="selectedProjectImage"
					:class="`project__img ${fade ? 'fade' : ''}`"
					:style="topPosition"
				>
			</ul>
		</div>
	</section>
</template>

<script>
	export default {
		data: () => ({
			timer: null,
			fade: false,
			hover: false,
			selectedProjectImage: '',
			topPosition: { top: 0 },
			romans: ['I', 'II', 'III', 'IV', 'V', 'VI', 'VII', 'VIII', 'IX', 'X'],
			projects: [
				{
					text: 'Matcha',
					img: 'matcha.gif'
				},
				{
					text: 'Hypertube',
					img: 'https://www.stevensegallery.com/640/360'
				},
				{
					text: 'Camagru',
					img: 'https://www.stevensegallery.com/642/360'
				},
				{
					text: 'Trackly',
					img: 'https://www.stevensegallery.com/640/362'
				}
			]
		}),
		methods: {
			hoverIn(i) {
				this.fade = false
				clearTimeout(this.timer)
				this.selectedProjectImage = this.projects[i].img
				this.topPosition.top = `${Math.round(
					((i + 0.6) * 100) / this.projects.length
				)}%`
				this.hover = true
			},
			hoverOut() {
				this.fade = true
				this.timer = setTimeout(() => {
					this.hover = false
					this.selectedProjectImage = ''
				}, 100)
			}
		}
	}
</script>


<style scoped>
	.projects__list {
		list-style: none;
		display: flex;
		flex-direction: column;
		padding: 0.5rem 0 0.5rem 6rem;
		font-weight: 700;
		font-size: 2rem;
		line-height: 1.5;
		align-items: flex-start;
		position: relative;
	}

	.projects__item {
		font-size: 2em;
		width: 100%;
		position: relative;
		margin: 0rem 0.5rem;
		padding: 1.5rem 0;
		z-index: 2;
		cursor: pointer;
	}

	.projects__roman {
		position: absolute;
		left: -6rem;
		padding-right: 6rem;
	}

	.projects__text {
		position: relative;
	}

	.projects__text::after {
		content: '';
		position: absolute;
		top: calc(50% - 2px);
		left: -6.5rem;
		width: calc(100% + 7rem);
		height: 2.5rem;
		pointer-events: none;
		background: var(--color-light);
		transition: transform 0.5s;
		transform: scale3d(0, 1, 1);
		transition-timing-function: cubic-bezier(0.8, 0, 0.2, 1);
		transform-origin: 100% 50%;
		z-index: -1;
	}

	.projects__item:hover > .projects__text::after,
	.projects__item:focus > .projects__text::after {
		transform: scale3d(1, 1, 1);
		transform-origin: 0% 50%;
	}

	.project__img {
		position: absolute;
		transition: all 0.3s ease-in;
		right: 0;
		animation: show 0.4s ease-in-out;
		transform: translateY(-50%);
		transform-origin: 50% 0%;
		max-width: 50%;
		opacity: 0.6;
		border-radius: 3px;
	}

	.project__img.fade {
		animation: fade 0.6s ease-in-out;
	}

	@keyframes show {
		0% {
			opacity: 0;
			transform: scale(0) translateY(-50%);
		}
		100% {
			opacity: 0.6;
			transform: scale(1) translateY(-50%);
		}
	}

	@keyframes fade {
		0% {
			opacity: 0.6;
			transform: scale(1) translateY(-50%);
		}
		100% {
			opacity: 0;
			transform: scale(0) translateY(-50%);
		}
	}
</style>
