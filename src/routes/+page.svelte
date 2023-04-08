<script lang="ts">
  import { browser } from '$app/environment'
  import { goto } from '$app/navigation';

  import NavBox from "$lib/components/NavBox.svelte";
  
  function routeToPage(route: string) {
		if (browser && route) {
			goto(route, {replaceState: false});
		}
	}
</script>

<div class="p-6 flex justify-center">
	<NavBox title={'Virtual Art Exhibit'} subTitle={'Explore virtual rooms'} on:click={() => routeToPage('/pages/art')} />
</div>
