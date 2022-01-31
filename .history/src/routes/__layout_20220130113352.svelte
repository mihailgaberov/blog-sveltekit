<script context="module" lang="ts">
	import type { LoadOutput } from '@sveltejs/kit'

	export const load = async ({ url }): Promise<LoadOutput> => {
		const path: string = url.pathname

		return {
			props: {
				path
			}
		}
	}
</script>

<script lang="ts">
  import '$lib/assets/scss/global.scss'
  import Header from '$lib/components/Header.svelte'
  import Footer from '$lib/components/Footer.svelte'
  import { currentPage, isLoading } from '$lib/data/store'
  import { navItems } from '$lib/config'
	import { prefetch } from '$app/navigation'
  import { onMount } from 'svelte'
  import Loader from '$lib/components/Loader.svelte'
  import PageTransition from '$lib/components/PageTransition.svelte';

  export let path
  
  const setLoading = (newState: boolean): void => {
		isLoading.set(newState)
	}

  $: currentPage.set(path)

  onMount(() => {
    navItems.forEach(item => prefetch(item.route))
  })
</script>

<div id="app">
	<Loader loading={$isLoading}/>

	<Header /> 

	<div class="layout"> 

		<PageTransition refresh={path}>
			<slot/>
		</PageTransition>
	</div>

	<Footer />
</div>
