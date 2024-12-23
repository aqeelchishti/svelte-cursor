<script lang="ts">
	let { children } = $props();
</script>

<svelte:head>
	<title>Svelte Swiftcursor</title>
</svelte:head>

{@render children()}

<style>
	:global(body) {
		cursor: none !important;
		margin: 0;
		padding: 0;
	}
</style>
