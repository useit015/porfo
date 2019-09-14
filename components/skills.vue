<template>
	<div class="skills__container">
		<canvas id="skills"></canvas>
	</div>
</template>

<script>
	import * as THREE from "three";
	import { TweenMax, Power1 } from "gsap";
	import noise from "@/assets/noise";

	export default {
		data: () => ({
			skills: [
				"HTML",
				"CSS",
				"JavaScript",
				"TypeScript",
				"REST",
				"JSON",
				"XML",
				"Angular",
				"Wordpress",
				"Node",
				"Git",
				"Bootstrap",
				"SASS",
				"RxJs",
				"jQuery",
				"NoSQl",
				"Karma",
				"Gulp",
				"npm",
				"Bower",
				"BEM"
			],
			sprites: [],
			scene: null,
			mesh: null,
			width: null,
			height: null,
			canvas: null,
			camera: null,
			geometry: null,
			material: null,
			renderer: null,
			resizeTimer: null,
			mouse: new THREE.Vector2(0.8, 0.5)
		}),
		computed: {
			rotationY() {
				return (this.mouse.x * 2 - 1) * 0.025;
			},
			rotationX() {
				return (this.mouse.y * 2 - 1) * 0.025;
			}
		},
		methods: {
			animate(a) {
				requestAnimationFrame(this.animate);
				this.mesh.rotation.x = this.rotationX;
				this.mesh.rotation.y = this.rotationY;
				this.sprites.forEach((cur, i) => {
					cur.position.applyQuaternion(this.mesh.quaternion);
				});
				this.renderer.render(this.scene, this.camera);
			},
			makeTextSprite(msg) {
				const canvas = document.createElement("canvas");
				const context = canvas.getContext("2d");
				context.font = `Bold 24px Roboto`;
				const metrics = context.measureText(msg);
				const x = (canvas.width - metrics.width) / 2;
				const y = canvas.height / 2 + 24 / 2;
				context.fillText(msg, x, y);
				const texture = new THREE.Texture(canvas);
				texture.needsUpdate = true;
				const spriteMaterial = new THREE.SpriteMaterial({
					map: texture,
					fog: true
				});
				const sprite = new THREE.Sprite(spriteMaterial);
				sprite.scale.set(100, 50, 1.0);
				return sprite;
			},
			addLight() {
				const light = new THREE.PointLight(0xffffff);
				light.position.set(0, 250, 0);
				this.scene.add(light);
			},
			addSphere() {
				this.geometry = new THREE.SphereGeometry(100, 6, 4);
				this.geometry.mergeVertices();
				this.material = new THREE.MeshNormalMaterial();
				this.material.opacity = 0;
				this.material.transparent = true;
				this.material.depthWrite = false;
				this.material.depthTest = false;
				this.mesh = new THREE.Mesh(this.geometry, this.material);
				this.mesh.renderDepth = 1e20;
				this.mesh.position.set(0, 0, 0);
				this.scene.add(this.mesh);
			},
			addSprites() {
				this.geometry.vertices.forEach((cur, i) => {
					const spritey = this.makeTextSprite(this.skills[i]);
					const { x, y, z } = cur.clone().multiplyScalar(1.1);
					spritey.position.set(x, y, z);
					this.scene.add(spritey);
					this.sprites.push(spritey);
				});
			},
			resize() {
				this.resizeTimer = clearTimeout(this.resizeTimer);
				this.resizeTimer = setTimeout(() => {
					this.canvas.style.width = "";
					this.canvas.style.height = "";
					this.width = this.canvas.offsetWidth;
					this.height = this.canvas.offsetHeight;
					this.camera.aspect = this.width / this.height;
					this.camera.updateProjectionMatrix();
					this.renderer.setSize(this.width, this.height);
				}, 100);
			},
			mouseMove(e) {
				TweenMax.to(this.mouse, 0.8, {
					y: e.clientY / this.height,
					x: e.clientX / this.width,
					ease: Power1.easeOut
				});
			},
			zoom(e) {
				e.preventDefault();
				if (e.deltaY > 0 && this.camera.position.z >= 700) return;
				if (e.deltaY < 0 && this.camera.position.z <= 400) return;
				this.camera.position.z += e.deltaY > 0 ? 10 : -10;
			},
			init() {
				this.canvas = document.querySelector("#skills");
				this.width = this.canvas.offsetWidth;
				this.height = this.canvas.offsetHeight;
				const ratio = this.width / this.height;
				this.renderer = new THREE.WebGLRenderer({
					canvas: this.canvas,
					antialias: true,
					alpha: true
				});
				this.renderer.setPixelRatio(window.devicePixelRatio > 1 ? 2 : 1);
				this.renderer.setSize(this.width, this.height);
				this.renderer.setClearColor(0xa9e7da, 0);
				this.scene = new THREE.Scene();
				this.scene.fog = new THREE.Fog(0xffffff, 150, 1000);
				this.camera = new THREE.PerspectiveCamera(45, ratio, 0.1, 20000);
				this.scene.add(this.camera);
				this.camera.position.set(0, 0, 400);
				this.addLight();
				this.addSphere();
				this.addSprites();
				window.addEventListener("resize", this.resize);
				this.canvas.addEventListener("mousewheel", this.zoom);
				this.canvas.addEventListener("mousemove", this.mouseMove);
				this.animate();
			}
		},
		mounted() {
			this.init();
		},
		beforeDestroy() {
			this.animate = () => {};
		}
	};
</script>

<style scoped>
	.skills__container {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	#skills {
		width: 90vmin;
		height: 90vmin;
		margin: 0 auto;
	}
</style>
