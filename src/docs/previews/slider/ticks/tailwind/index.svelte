<script lang="ts">
	import { createSlider, melt } from '$lib/index.js';

	const {
		elements: { root, range, thumb, tick },
		states: { ticks },
	} = createSlider({
		defaultValue: [5],
		min: 0,
		step: 1,
		max: 10,
	});
</script>

<span use:melt={$root} class="relative flex h-[20px] w-[200px] items-center">
	<span class="block h-[3px] w-full bg-black/40">
		<span use:melt={$range} class="h-[3px] bg-white" />
	</span>

	<span
		use:melt={$thumb()}
		class="z-10 block h-5 w-5 rounded-full bg-white focus:ring-4 focus:ring-black/40"
	/>

	{#each { length: $ticks } as _}
		<span
			use:melt={$tick()}
			class="h-[3px] w-[3px] rounded-full bg-white/50 data-[bounded]:bg-magnum-800/75"
		/>
	{/each}
</span>
