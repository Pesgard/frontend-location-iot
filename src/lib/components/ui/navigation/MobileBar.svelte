<script lang="ts">
	import { BikeIcon, BookIcon, HouseIcon, TreePalmIcon } from '@lucide/svelte';
	import { Navigation } from '@skeletonlabs/skeleton-svelte';

	let { children } = $props();

	const links = [
		{ label: 'Home', href: '#', icon: HouseIcon },
		{ label: 'Entertainment', href: '#', icon: BookIcon },
		{ label: 'Recreation', href: '#', icon: BikeIcon },
		{ label: 'Relaxation', href: '#', icon: TreePalmIcon }
	];
	let anchorBar = 'btn hover:preset-tonal flex-col items-center gap-1';
</script>

<div class="w-full h-full grid grid-rows-[1fr_auto]">
	<div class="overflow-auto">
		{@render children?.()}
	</div>
	<!-- --- -->
	<Navigation layout="bar" class="border-t border-surface-200-800">
		<Navigation.Menu class="grid grid-cols-4 gap-2">
			{#each links as link (link)}
				{@const Icon = link.icon}
				<a href={link.href} class={anchorBar}>
					<Icon class="size-5" />
					<span class="text-[10px]">{link.label}</span>
				</a>
			{/each}
		</Navigation.Menu>
	</Navigation>
	<!-- --- -->
</div>