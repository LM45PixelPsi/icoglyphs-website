<script>
	import icoGlyphs from '$lib/index.js';
	import { goto } from '$app/navigation';
	import globalVarFront from '$lib/globalVarFront.svelte.js';

	let { icoGlyphName } = $props();

	// $inspect(icoGlyphName);
</script>

{#if globalVarFront.showPrivateIcoGlyph.value || !icoGlyphName.startsWith('_')}
	<button
		onclick={() => goto(`/ico/${icoGlyphName}`)}
		aria-label={`Navigate to ${icoGlyphName} page`}
		class="icoglyphContainer"
	>
		<svg {...icoGlyphs.getSvgAttributes(icoGlyphName)}>
			<path d={icoGlyphs.getPath(icoGlyphName)} />
		</svg>
	</button>
{/if}

<style>
	svg {
		stroke-width: 3px;
		stroke: rgb(233, 208, 208);
		fill: none;
	}
	.icoglyphContainer {
		width: 150px;
		height: 150px;

		border: rgb(141, 116, 116) 2px solid;
		margin: 5px;
		border-radius: 5%;
	}
</style>
