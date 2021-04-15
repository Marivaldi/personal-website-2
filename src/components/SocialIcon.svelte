<script>
	export let linkToSocial = "";
	export let onClick = () => {};
	export let fontAwesomeClass = "";
	export let linkText = "";
</script>

{#if linkToSocial === ""}
	<!-- svelte-ignore a11y-missing-attribute -->
	<a class="icon grow" on:click={onClick}>
		<i class={fontAwesomeClass} />
		<div class="icon-text">{linkText}</div>
	</a>
{:else}
	<a href={linkToSocial} class="icon grow" on:click={onClick}>
		<i class={fontAwesomeClass} />
		<div class="icon-text">{linkText}</div>
	</a>
{/if}

<style>
	.icon {
		font-size: 2.2rem;
		padding: 10px;
		display: inline-block;
	}

	.icon-text {
		font-size: 1.3rem;
		font-family: "Barlow", sans-serif;
	}
</style>
