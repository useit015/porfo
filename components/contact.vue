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
				<button class="send__btn">Send</button>
			</div>
		</div>
	</section>
</template>

<script>
	export default {};
</script>

<style scoped>
.form {
	display: flex;
	justify-content: center;
	align-items: center;
	flex-wrap: wrap;
	padding: 5rem 0;
}

.input {
	position: relative;
	display: inline-block;
	margin: 1rem 2rem 2rem;
	flex: 1 1 calc(100% - 2rem);
}

.input.name,
.input.email {
	flex: 1 1 calc(50% - 4rem);
}

.input > input,
.input > textarea {
	padding: 1.2rem 2rem;
	font-size: 2rem;
	font-weight: 700;
	line-height: 1.5;
	letter-spacing: 2px;
	background: #00000033;
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
	content: "";
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
}

.send__btn:hover {
	background: #00000022;
	outline: none;
}

.send__btn:focus {
	outline: none;
}
</style>
