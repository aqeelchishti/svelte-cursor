<script lang="ts">
	let { cSize = 20, cColor = 'black', cShape = 'circle', hoverAnimate = false } = $props();

	let x = $state(-100);
	let y = $state(-100);

	const cx = $derived(cSize / 2);
	const cy = $derived(cSize / 2);

	$effect(() => {
		const hoverables = document.querySelectorAll('.hoverable, a, button');
		hoverables.forEach((hoverable) => {
			hoverable.addEventListener('mouseenter', () => {
				cSize += hoverAnimate === true ? 20 : 0;
				document.body.style.cursor = 'none';
			});
			hoverable.addEventListener('mouseleave', () => {
				cSize -= hoverAnimate === true ? 20 : 0;
			});
		});
	});
</script>

<svelte:window
	onmousemove={(e) => {
		x = e.clientX;
		y = e.clientY;
	}}
/>

<div
	class="custom-cursor {cShape}"
	style="left: {x - cx}px; top: {y - cy}px; --size:{cSize}px; --background-color: {cColor}"
></div>

<style>
	:global(body) {
		cursor: none;
	}

	.custom-cursor {
		--background-color: 'black';
		--size: 20;
		background-color: var(--background-color);
		width: var(--size);
		height: var(--size);
		position: fixed;
		border-radius: 50%;
		pointer-events: none;
		z-index: 99999;
		/* Customize your cursor styles here */
		transition: all 0.1s cubic-bezier(0.175, 0.885, 0.32, 1.275);
		cursor: none;
	}

	.custom-cursor.square {
		border-radius: 0;
	}
	.cursor-none {
		cursor: none;
	}
</style>
