<script lang="ts">
  import { isMenuOpen } from '$lib/data/store'
  import HamburgerSVG from './svg/HamburgerSVG.svelte'
  import XSVG from './svg/XSVG.svelte'

  export let closeOnly

  const toggleIsMenuOpen = () => {
    isMenuOpen.set(!$isMenuOpen)
  }
</script>

<button
  on:click={toggleIsMenuOpen}
  aria-pressed={$isMenuOpen}
  class="menu-button"
  tabindex={($isMenuOpen || !closeOnly) ? 0 : -1}
>
  <span class="sr">Toggle hamburger menu</span>
  {#if closeOnly}
    <XSVG />
  {:else}
    <HamburgerSVG />
  {/if}
</button>
