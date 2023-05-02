<script lang="ts">
	// The ordering of these imports is critical to your app working properly
	import '@skeletonlabs/skeleton/themes/theme-crimson.css';
	// If you have source.organizeImports set to true in VSCode, then it will auto change this ordering
	import '@skeletonlabs/skeleton/styles/all.css';
	// Most of your app wide CSS should be put in this file
	import '../app.postcss';

	import { AppRail, AppRailTile, AppShell, Avatar } from '@skeletonlabs/skeleton';
	import { writable, type Writable } from 'svelte/store';
	import { filter, Emerald } from '@skeletonlabs/skeleton';

	const storeValue: Writable<number> = writable(0);
</script>

<AppShell>
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
				<AppRailTile label="Profile" value={1} tag="a">
					<Avatar
						src="https://i.pravatar.cc/100?img=3"
						width="w-12"
						style="filter: url({'#Emerald'})"
					/>
				</AppRailTile>
			</svelte:fragment>
		</AppRail>
	</svelte:fragment>

	<!-- Router Slot -->
	<slot />
	<!-- ---- / ---- -->
</AppShell>
