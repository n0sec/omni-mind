<script lang="ts">
	// The ordering of these imports is critical to your app working properly
	import '@skeletonlabs/skeleton/themes/theme-crimson.css';
	// If you have source.organizeImports set to true in VSCode, then it will auto change this ordering
	import '@skeletonlabs/skeleton/styles/all.css';
	// Most of your app wide CSS should be put in this file
	import '../app.postcss';

	import { AppBar, AppRail, AppRailTile, AppShell, LightSwitch } from '@skeletonlabs/skeleton';
	import { writable, type Writable } from 'svelte/store';
	import logo from '$lib/assets/logo.png';

	const storeValue: Writable<number> = writable(0);
	export let loggedIn: boolean = false;
</script>

<svelte:head>
	<title>OmniMind</title>
</svelte:head>

<AppShell>
	<svelte:fragment slot="header">
		<!-- AppBar with Light Switch-->
		<AppBar class="w-full">
			<svelte:fragment slot="lead">
				<!-- Logo -->
				<img src={logo} alt="Omni-Mind Logo" class="w-12 h-12 mr-2" />
				<h1 class="unstyled text-xl font-bold">OmniMind</h1>
			</svelte:fragment>
			<svelte:fragment slot="trail">
				<LightSwitch />
				<!-- ?? Does this look too weird?-->
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<svelte:fragment slot="sidebarLeft">
		<AppRail selected={storeValue} trail={1}>
			<!-- Left Sidebar Content -->
			<AppRailTile label="Home" value={0} tag="a" href="/"
				><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"
					><path fill="currentColor" d="M10 20v-6h4v6h5v-8h3L12 3L2 12h3v8h5Z" /></svg
				></AppRailTile
			>
			<!-- Profile icon -->
			<svelte:fragment slot="trail">
				{#if (loggedIn = true)}
					<AppRailTile label="Profile" value={1} tag="a">
						<svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"
							><path
								fill="currentColor"
								d="M12 19.2c-2.5 0-4.71-1.28-6-3.2c.03-2 4-3.1 6-3.1s5.97 1.1 6 3.1a7.232 7.232 0 0 1-6 3.2M12 5a3 3 0 0 1 3 3a3 3 0 0 1-3 3a3 3 0 0 1-3-3a3 3 0 0 1 3-3m0-3A10 10 0 0 0 2 12a10 10 0 0 0 10 10a10 10 0 0 0 10-10c0-5.53-4.5-10-10-10Z"
							/></svg
						>
					</AppRailTile>
				{/if}
			</svelte:fragment>
		</AppRail>
	</svelte:fragment>

	<!-- A floating action button in the bottom right -->
	<button type="button" class="btn-icon btn-icon-xl variant-filled absolute bottom-6 right-6"
		><svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"
			><path fill="currentColor" d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2Z" /></svg
		></button
	>

	<!-- Router Slot -->
	<slot />
	<!-- ---- / ---- -->
</AppShell>
