<template>
	<section class="projects">
		<div class="container">
			<h2 class="subtitle">— Work</h2>
			<ul class="projects__list">
				<li class="projects__item">Matcha</li>
				<li class="projects__item">Hypertube</li>
				<li class="projects__item">Camagru</li>
				<li class="projects__item">Trackly</li>
			</ul>
		</div>
	</section>
</template>

<style>
	.projects__list {
		list-style: none;
		display: flex;
		flex-direction: column;
		padding: 0.5rem 5rem;
		font-weight: 700;
		font-size: 2rem;
		line-height: 1.5;
		align-items: flex-start;
	}

	.projects__item {
		font-size: 2em;
		position: relative;
		margin: 1rem 0.5rem;
		z-index: 2;
		cursor: pointer;
	}

	.projects__item::before {
		position: absolute;
		left: -5.5rem;
		padding-right: 5rem;
	}

	.projects__item:nth-child(1):before {
		content: "I.";
	}

	.projects__item:nth-child(2):before {
		content: "II.";
	}

	.projects__item:nth-child(3):before {
		content: "III.";
	}

	.projects__item:nth-child(4):before {
		content: "IV.";
	}

	.projects__item:nth-child(5):before {
		content: "V.";
	}

	.projects__item:nth-child(6):before {
		content: "VI.";
	}

	.projects__item::after {
		content: "";
		position: absolute;
		top: calc(50% - 2px);
		left: -5.5rem;
		width: calc(100% + 5.5rem);
		height: 2.5rem;
		pointer-events: none;
		background: var(--color-light);
		transition: transform 0.5s;
		transform: scale3d(0, 1, 1);
		transition-timing-function: cubic-bezier(0.8, 0, 0.2, 1);
		transform-origin: 100% 50%;
		z-index: -1;
	}

	.projects__item:hover::after,
	.projects__item:focus::after {
		transform: scale3d(1, 1, 1);
		transform-origin: 0% 50%;
	}
</style>
