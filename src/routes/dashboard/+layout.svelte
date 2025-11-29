<script lang="ts">
	import Sidebar from '$lib/components/ui/navigation/Sidebar.svelte';
	import MobileBar from '$lib/components/ui/navigation/MobileBar.svelte';

	let { children } = $props();

	let isMobile = $state(false);

	function checkMobile() {
		isMobile = window.innerWidth <= 640;
	}

	$effect(() => {
		// Verificar al montar
		checkMobile();

		// Escuchar cambios de tamaño de pantalla
		window.addEventListener('resize', checkMobile);

		// Cleanup al desmontar
		return () => {
			window.removeEventListener('resize', checkMobile);
		};
	});
</script>

<div class="h-screen w-full">
	{#if isMobile}
		<MobileBar>
			{@render children()}
		</MobileBar>
	{:else}
		<Sidebar>
			{@render children()}
		</Sidebar>
	{/if}
</div>
