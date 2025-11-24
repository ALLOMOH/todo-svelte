<script>
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
	let tile = "todo list app";
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>{tile}</title>
</svelte:head>

{@render children()}
