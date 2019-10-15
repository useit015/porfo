<template>
	<section class="contact">
		<div class="container">
			<h2 class="subtitle">— Contact Me</h2>
			<div class="form">
				<div class="input name">
					<input type="text" placeholder="Name">
				</div>
				<div class="input email">
					<input type="text" placeholder="Email">
				</div>
				<div class="input company">
					<input type="text" placeholder="Company / Organization">
				</div>
				<div class="input company">
					<textarea rows="7" placeholder="Project details"></textarea>
				</div>
				<button class="send__btn" @click="ripple">
					Send
					<span
						:class="`send__btn-ripple ${show ? 'animate' : ''}`"
						:style="{top:`${y}px`, left: `${x}px`}"
					></span>
				</button>
			</div>
		</div>
	</section>
</template>

<script>
	export default {
		data: () => ({
			x: 0,
			y: 0,
			show: false,
			timer: null
		}),
		methods: {
			ripple(e) {
				clearTimeout(this.timer)
				this.x = e.offsetX
				this.y = e.offsetY
				this.show = true
				this.timer = setTimeout(() => (this.show = false), 350)
			}
		}
	}
</script>

<style scoped>
	.form {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-wrap: wrap;
		padding: 2.5rem 0 5rem;
	}

	.input {
		position: relative;
		display: inline-block;
		margin: 1rem 0 2rem;
		flex: 1 1 calc(100% - 2rem);
	}

	.input.name,
	.input.email {
		flex: 1 1 calc(50% - 4rem);
	}

	.input.name {
		margin-right: 1rem;
	}

	.input.email {
		margin-left: 1rem;
	}

	.input > input,
	.input > textarea {
		padding: 1.2rem 2rem;
		font-size: 2rem;
		font-weight: 700;
		line-height: 1.5;
		letter-spacing: 2px;
		background: #00000015;
		box-shadow: none;
		border: none;
		width: 100%;
		resize: none;
	}

	.input > input::-webkit-input-placeholder,
	.input > textarea::-webkit-input-placeholder {
		color: var(--color-dark);
	}

	.input > textarea::-webkit-scrollbar {
		width: 0.8rem;
	}

	.input > textarea::-webkit-scrollbar-thumb {
		background-color: var(--color-dark);
	}

	.input::after {
		content: '';
		position: absolute;
		bottom: 0;
		left: 0;
		width: 100%;
		height: 0.3rem;
		pointer-events: none;
		background: var(--color-dark);
		transition: transform 0.25s ease-out;
		transform: scale3d(0, 1, 1);
		transform-origin: 0% 50%;
	}

	.input > input:focus,
	.input > textarea:focus {
		outline: none;
	}

	.input:focus-within::after {
		transform: scale3d(1, 1, 1);
	}

	.send__btn {
		margin: 2.5rem 0 0;
		cursor: pointer;
		padding: 1rem 3rem;
		font-size: 2.5rem;
		font-weight: 700;
		line-height: 1;
		letter-spacing: 2px;
		background: transparent;
		box-shadow: none;
		border: 1px solid var(--color-dark);
		transition: all 0.2s ease-out;
		overflow: hidden;
		position: relative;
	}

	.send__btn:hover {
		background: #00000010;
		outline: none;
	}

	.send__btn:focus {
		outline: none;
	}

	.send__btn-ripple {
		position: absolute;
		transform: translate(-50%, -50%) scale(0);
		display: inline-block;
		border-radius: 50%;
		width: 105%;
		height: 220%;
		background: #00000022;
		transition: transform 0.3s ease-in, opacity 0.3s ease-in-out;
		opacity: 0;
	}

	.send__btn-ripple.animate {
		opacity: 1;
		transform: translate(-50%, -50%) scale(2);
	}
</style>
