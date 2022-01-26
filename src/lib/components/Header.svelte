<script>
  import MainNav from './MainNav.svelte'
  import HamburgerMenuButton from './HamburgerMenuButton.svelte'
  import { siteTitle } from '$lib/config'

  const focusMain = () => {
		const main = document.querySelector('main');
		main.focus();
	}
</script>

<header>
  <a on:click|preventDefault={focusMain} class="skip-to-content-link" href="#main">
    Skip to main content
  </a>

  <svg class="background--custom" id="demo" viewBox="0 0 100 100" preserveAspectRatio="none">
    <path fill="#d56d3b" fill-opacity="0.5" d="M-100 -100L200 -100L200 50L-100 50Z" style="animation: path0 25s linear infinite alternate;" /><path fill="#ccff00" fill-opacity="0.8" d="M-100 -100L200 -100L200 50L-100 50Z" style="animation: path1 3.1055900621118013s linear infinite alternate;" /><path fill="#6efeb0" fill-opacity="0.4" d="M-100 -100L200 -100L200 50L-100 50Z" style="animation: path2 19.23076923076923s linear infinite alternate;" />
  </svg>
  
  <a href="/" class="site-title">
    {siteTitle}
  </a>
  
  <HamburgerMenuButton />
  <MainNav />

</header>