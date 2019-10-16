<template>
	<canvas id="scene"></canvas>
</template>

<script>
	import * as THREE from 'three'
	import { TweenMax, Power1 } from 'gsap'
	import noise from '@/assets/noise'

	export default {
		data: () => ({
			scene: null,
			shape: null,
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
		methods: {
			animate(a) {
				requestAnimationFrame(this.animate)
				this.updateVertices(a)
				this.updatePositions()
				this.renderer.render(this.scene, this.camera)
			},
			updatePositions() {
				const [x, y] = [this.mouse.x, this.mouse.y].map(cur => (0.5 - cur) * 50)
				this.camera.position.x = x
				this.camera.position.y = -y
				this.shape.position.x = -x
				this.shape.position.y = y
			},
			updateVertices(a) {
				this.geometry.vertices.forEach(cur => {
					cur.copy(cur._o)
					const perlin = noise.simplex3(
						cur.x * 0.005 + a * 0.0002,
						cur.y * 0.005 + a * 0.0003,
						cur.z * 0.005
					)
					cur.multiplyScalar(perlin * 0.4 * (0.5 - this.mouse.y) + 0.8)
				})
				this.geometry.verticesNeedUpdate = true
			},
			addLight() {
				const light = new THREE.HemisphereLight(0xffffff, 0x0c056d, 0.7)
				const light1 = new THREE.DirectionalLight(0x590d82, 0.5)
				const light2 = light1.clone()
				light1.position.set(200, 300, 400)
				light2.position.set(-200, 300, 400)
				this.scene.add(light)
				this.scene.add(light1)
				this.scene.add(light2)
			},
			addShape() {
				this.geometry = new THREE.IcosahedronGeometry(120, 4)
				this.geometry.vertices.forEach(cur => (cur._o = cur.clone()))
				this.material = new THREE.MeshPhongMaterial({
					emissive: 0x23f660,
					emissiveIntensity: 0.4,
					shininess: 0
				})
				this.shape = new THREE.Mesh(this.geometry, this.material)
				this.scene.add(this.shape)
			},
			resize() {
				this.resizeTimer = clearTimeout(this.resizeTimer)
				this.resizeTimer = setTimeout(() => {
					this.canvas.style.width = ''
					this.canvas.style.height = ''
					this.width = this.canvas.offsetWidth
					this.height = this.canvas.offsetHeight
					this.camera.aspect = this.width / this.height
					this.camera.updateProjectionMatrix()
					this.renderer.setSize(this.width, this.height)
				}, 100)
			},
			mouseMove(e) {
				TweenMax.to(this.mouse, 0.8, {
					y: e.clientY / this.height,
					x: e.clientX / this.width,
					ease: Power1.easeOut
				})
			},
			init() {
				this.canvas = document.querySelector('#scene')
				this.width = this.canvas.offsetWidth
				this.height = this.canvas.offsetHeight
				const ratio = this.width / this.height
				this.renderer = new THREE.WebGLRenderer({
					canvas: this.canvas,
					antialias: true,
					alpha: true
				})
				this.renderer.setPixelRatio(window.devicePixelRatio > 1 ? 2 : 1)
				this.renderer.setSize(this.width, this.height)
				this.renderer.setClearColor(0xa9e7da, 0)
				this.scene = new THREE.Scene()
				this.camera = new THREE.PerspectiveCamera(100, ratio, 0.1, 10000)
				this.camera.position.set(10, 0, 200)
				this.addLight()
				this.addShape()
				window.addEventListener('resize', this.resize)
				window.addEventListener('mousemove', this.mouseMove)
				this.animate()
			}
		},
		mounted() {
			this.init()
		},
		beforeDestroy() {
			this.animate = () => {}
		}
	}
</script>

<style scoped>
	#scene {
		position: absolute;
		top: 0;
		left: 0;
		width: 100vw;
		height: 100vh;
	}
</style>
