<script lang="ts">
	import { onMount } from 'svelte';

	let {
		size = 20,
		color = 'black',
		shape = 'circle',
		mixBlendMode = 'none',
		onHoverAnimate = false
	} = $props();

	let x = $state(-100);
	let y = $state(-100);

	const cx = $derived(size / 2);
	const cy = $derived(size / 2);

	onMount(() => {
		const initCursor = () => {
			document.addEventListener('mousemove', (e) => {
				x = e.clientX;
				y = e.clientY;
			});
			if (onHoverAnimate === true) {
				const hoverables = document.querySelectorAll('.hoverable, a, button');
				hoverables.forEach((hoverable) => {
					hoverable.addEventListener('mouseenter', () => {
						size += 20;
						document.body.style.cursor = 'none';
					});
					hoverable.addEventListener('mouseleave', () => {
						size -= 20;
					});
				});
			}
		};

		initCursor();
	});
</script>

<!--
<svelte:window
	onmousemove={(e) => {
		x = e.clientX;
		y = e.clientY;
	}}
/>
-->

<div
	class="custom-cursor {shape}"
	style="left: {x - cx}px; top: {y -
		cy}px;--size:{size}px; --mix-blend-mode: {mixBlendMode}; --background-color: {color}"
></div>

<!--
<Cursor color="#0097b280" mixBlendMode="normal" size={32} shape="square" />
<Cursor color="#0097b2" mixBlendMode="normal" size={12} shape="square" />
-->

<style>
	:global(body) {
		cursor: none;
	}

	.custom-cursor {
		--background-color: 'black';
		--mix-blend-mode: 'none';
		--size: 20;
		background-color: var(--background-color);
		mix-blend-mode: var(--mix-blend-mode);
		width: var(--size);
		height: var(--size);
		position: fixed;
		border-radius: 50%;
		pointer-events: none;
		z-index: 99999;
		/* Customize your cursor styles here */
		transition: all 0.2s cubic-bezier(0.28, 0.8, 0.36, 1);
		cursor: none;
	}

	.custom-cursor.square {
		border-radius: 0;
	}
	.cursor-none {
		cursor: none;
	}
</style>
